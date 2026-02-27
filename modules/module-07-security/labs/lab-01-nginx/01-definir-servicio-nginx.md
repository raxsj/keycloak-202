# Lab 01 — NGINX Reverse Proxy

## Paso 01 — Definir servicio NGINX en Docker Compose

---

## 🎯 Objetivo

Añadir un servicio NGINX que actúe como reverse proxy delante de Keycloak.

---

## 🧠 Contexto

En entornos reales:

* Keycloak no suele exponerse directamente.
* Se coloca detrás de un reverse proxy.
* El proxy gestiona:

  * TLS
  * Headers
  * Reescritura
  * Balanceo

En este laboratorio simularemos ese escenario.

---

## 📍 Ubicación

Editar:

```
infra/docker-compose.yml
```

---

## ➕ Añadir servicio NGINX

Dentro de `services:` añadir:

```yaml id="z9x3op"
  nginx:
    image: nginx:latest
    container_name: nginx
    ports:
      - "8081:80"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - keycloak
    restart: always
```

---

## 📁 Crear estructura de configuración

Crear carpeta:

```
infra/nginx
```

---

## 📁 Crear archivo de configuración

Crear:

```
infra/nginx/nginx.conf
```

Contenido base:

```nginx id="o1pt7k"
events {}

http {
  server {
    listen 80;

    location / {
      proxy_pass http://keycloak:8080;
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

```bash id="e6nqv3"
docker compose down
docker compose up -d
```

---

## 🌐 Validar acceso

Abrir en navegador:

```
http://localhost:8081
```

Debe mostrarse la pantalla de Keycloak.

---

## 🧠 Qué estamos validando

* NGINX actúa como proxy.
* Keycloak queda detrás del reverse proxy.
* El tráfico pasa por NGINX.
* Preparado para configurar headers en el siguiente paso.
