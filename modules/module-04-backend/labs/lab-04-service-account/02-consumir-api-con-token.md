# Lab 04 — Service Account

## Paso 02 — Consumir API usando Client Credentials

---

## 🎯 Objetivo

Obtener un `access_token` usando el flujo **Client Credentials** y consumir la API protegida sin usuario interactivo.

---

## 🧠 Contexto

En este flujo:

* No hay login.
* No hay navegador.
* El backend-service se autentica usando:

  * client_id
  * client_secret

---

## 🔑 Obtener access_token

Desde terminal ejecutar:

```bash
curl -X POST \
  http://localhost:8080/realms/training/protocol/openid-connect/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=client_credentials" \
  -d "client_id=backend-service" \
  -d "client_secret=TU_CLIENT_SECRET"
```

Reemplazar `TU_CLIENT_SECRET` por el valor copiado en el paso anterior.

---

## 📦 Respuesta esperada

Debe devolver algo similar a:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expires_in": 300,
  "token_type": "Bearer"
}
```

Copiar el `access_token`.

---

## 🧪 Consumir endpoint protegido

Ejecutar:

```bash
curl -H "Authorization: Bearer TU_ACCESS_TOKEN" \
http://localhost:3000/protected
```

---

## 🔎 Resultado esperado

* Si el cliente tiene roles asignados → 200 OK.
* Si no tiene roles suficientes → 403.

---

## 🧠 Validación técnica

Este token:

* No contiene `preferred_username`
* Representa al cliente `backend-service`
* Incluye roles asignados al service account

---

## 🧠 Qué estamos validando

* Funcionamiento de Client Credentials Flow.
* Autenticación service-to-service.
* Validación JWT sin usuario humano.
* Autorización basada en roles del cliente.
