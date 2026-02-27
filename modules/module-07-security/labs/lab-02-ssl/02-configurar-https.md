# Lab 02 — SSL

## Paso 02 — Configurar HTTPS en NGINX

---

## 🎯 Objetivo

Configurar NGINX para servir tráfico HTTPS utilizando el certificado autofirmado generado.

---

## 📍 Editar docker-compose

Abrir:

```
infra/docker-compose.yml
```

Modificar el servicio `nginx` para montar los certificados:

```yaml id="g8x3kp"
  nginx:
    image: nginx:latest
    container_name: nginx
    ports:
      - "8081:80"
      - "8443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
      - ./nginx/certs:/etc/nginx/certs
    depends_on:
      - keycloak
    restart: always
```

---

## 📍 Editar configuración NGINX

Abrir:

```
infra/nginx/nginx.conf
```

Reemplazar por:

```nginx id="m2q7te"
events {}

http {

  server {
    listen 80;
    return 301 https://$host:8443$request_uri;
  }

  server {
    listen 443 ssl;

    ssl_certificate     /etc/nginx/certs/server.crt;
    ssl_certificate_key /etc/nginx/certs/server.key;

    location / {
      proxy_pass http://keycloak:8080;

      proxy_set_header Host $host:8443;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto https;
    }
  }
}
```

---

## ▶️ Reiniciar entorno

Desde:

```
infra/
```

Ejecutar:

```bash id="w3lm8q"
docker compose down
docker compose up -d
```

---

## 🌐 Probar acceso HTTPS

Abrir en navegador:

```
https://localhost:8443
```

El navegador mostrará advertencia de certificado no confiable.

Aceptar el riesgo y continuar.

---

## 🔎 Resultado esperado

* Redirección automática de HTTP a HTTPS.
* Login accesible por HTTPS.
* No errores de redirección infinita.

---

## 🧠 Qué estamos validando

* TLS activo en reverse proxy.
* Keycloak funcionando detrás de HTTPS.
* Headers correctos con `X-Forwarded-Proto https`.
* Arquitectura lista para entornos productivos reales.
