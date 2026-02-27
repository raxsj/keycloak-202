# Lab 01 — NGINX Reverse Proxy

## Paso 02 — Configurar correctamente el Proxy

---

## 🎯 Objetivo

Configurar NGINX para reenviar correctamente los headers necesarios cuando Keycloak está detrás de un reverse proxy.

---

## 🧠 Contexto

Keycloak necesita recibir correctamente:

* Host
* X-Forwarded-For
* X-Forwarded-Proto

Sin estos headers pueden producirse:

* Problemas con redirecciones
* URLs incorrectas
* Errores en issuer
* Problemas con cookies

---

## 📍 Editar configuración NGINX

Abrir:

```
infra/nginx/nginx.conf
```

Reemplazar el contenido por:

```nginx id="k7rz2p"
events {}

http {
  server {
    listen 80;

    location / {
      proxy_pass http://keycloak:8080;

      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
  }
}
```

---

## 📍 Ajustar Keycloak para proxy

Editar el servicio `keycloak` en:

```
infra/docker-compose.yml
```

Añadir en `environment`:

```yaml id="e2v6tn"
      KC_PROXY: edge
      KC_HTTP_ENABLED: "true"
      KC_HOSTNAME_STRICT: "false"
```

---

## ▶️ Reiniciar entorno

Desde:

```
infra/
```

Ejecutar:

```bash id="n4z2ya"
docker compose down
docker compose up -d
```

---

## 🌐 Validar funcionamiento

Acceder a:

```
http://localhost:8081
```

Intentar iniciar sesión.

---

## 🔎 Resultado esperado

* No hay errores de redirección.
* El login funciona correctamente.
* Las URLs generadas son coherentes.

---

## 🧠 Qué estamos validando

* Proxy reenvía headers correctamente.
* Keycloak interpreta que está detrás de proxy.
* El sistema está listo para añadir HTTPS en el siguiente laboratorio.
