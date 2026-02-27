# Lab 03 — Proteger Endpoints

## Paso 03 — Testear autorización con curl

---

## 🎯 Objetivo

Validar desde terminal el comportamiento de los endpoints protegidos por rol y por scope.

---

## 🔑 Obtener un access_token válido

Desde la aplicación Angular (con usuario autenticado):

En consola del navegador:

```javascript
getKeycloakInstance().token
```

Copiar el `access_token`.

---

## 🧪 1️⃣ Probar endpoint protegido por rol

Ejecutar:

```bash
curl -H "Authorization: Bearer TU_ACCESS_TOKEN" \
http://localhost:3000/protected
```

### Resultado esperado

* Si el usuario tiene rol `admin` → 200 OK.
* Si no lo tiene → 403 Insufficient role.

---

## 🧪 2️⃣ Probar endpoint protegido por scope

Ejecutar:

```bash
curl -H "Authorization: Bearer TU_ACCESS_TOKEN" \
http://localhost:3000/scoped
```

### Resultado esperado

* Si el token contiene `api.read` → 200 OK.
* Si no lo contiene → 403 Insufficient scope.

---

## 🧪 3️⃣ Probar sin token

```bash
curl http://localhost:3000/protected
```

Resultado esperado:

```json
{ "error": "Missing Authorization header" }
```

---

## 🧪 4️⃣ Probar token manipulado

Modificar un carácter del token y ejecutar:

```bash
curl -H "Authorization: Bearer TOKEN_MODIFICADO" \
http://localhost:3000/protected
```

Resultado esperado:

```json
{ "error": "Invalid token" }
```

---

## 🧠 Qué estamos validando

* Firma del JWT.
* Issuer correcto.
* Validación por rol.
* Validación por scope.
* Respuesta adecuada ante tokens inválidos o ausentes.
* El backend aplica autenticación y autorización correctamente.
