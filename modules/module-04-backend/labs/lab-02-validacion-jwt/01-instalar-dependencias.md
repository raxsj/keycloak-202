# Lab 02 — Validación JWT

## Paso 01 — Instalar dependencias para validar tokens

---

## 🎯 Objetivo

Instalar las librerías necesarias para validar JWT emitidos por Keycloak usando JWKS.

---

## 📍 Ubicación

Desde:

```
apps/api-node
```

---

## 📦 Instalar dependencias

Ejecutar:

```bash id="2v9kqm"
npm install jsonwebtoken jwks-rsa
```

---

## 🔎 Qué hace cada librería

* `jsonwebtoken` → Permite verificar y decodificar JWT.
* `jwks-rsa` → Permite obtener la clave pública desde el endpoint JWKS de Keycloak.

---

## 📁 Verificar instalación

En `package.json` deben aparecer:

```json id="8qz7mv"
"jsonwebtoken": "...",
"jwks-rsa": "..."
```

---

## 🧠 Estado actual

* El backend puede verificar firmas JWT.
* Está preparado para validar tokens RS256.
* En el siguiente paso crearemos un middleware de autenticación.
