# Lab 02 — SSL

## Paso 01 — Generar certificado autofirmado

---

## 🎯 Objetivo

Generar un certificado TLS autofirmado para habilitar HTTPS en NGINX.

---

## 📍 Ubicación

Dentro de:

```
infra/nginx
```

Crear carpeta:

```
infra/nginx/certs
```

---

## 🔐 Generar clave privada

Ejecutar:

```bash
openssl genrsa -out infra/nginx/certs/server.key 2048
```

---

## 🔐 Generar certificado autofirmado

Ejecutar:

```bash
openssl req -new -x509 -key infra/nginx/certs/server.key \
-out infra/nginx/certs/server.crt \
-days 365 \
-subj "/C=ES/ST=Valencia/L=Valencia/O=Training/CN=localhost"
```

---

## 📁 Verificar archivos generados

Deben existir:

```
infra/nginx/certs/server.key
infra/nginx/certs/server.crt
```

---

## 🧠 Qué hemos hecho

* Generado clave privada RSA.
* Creado certificado autofirmado válido por 365 días.
* Preparado NGINX para servir tráfico HTTPS.

En el siguiente paso configuraremos NGINX para usar este certificado.
