# Lab 02 — Validación JWT

## Paso 03 — Validar firma usando JWKS

---

## 🎯 Objetivo

Probar que el backend valida correctamente la firma del JWT utilizando la clave pública obtenida desde el endpoint JWKS de Keycloak.

---

## 🧠 Contexto

Keycloak firma los tokens con RS256.
La clave pública se expone en:

```
http://localhost:8080/realms/training/protocol/openid-connect/certs
```

Nuestro middleware obtiene dinámicamente la clave correcta usando el `kid` del token.

---

## 🔑 Obtener un access_token válido

Desde la SPA Angular:

1. Accede a `/protected`.
2. Abre DevTools → Application → Storage.
3. Copia el `access_token`.

O bien desde consola:

```javascript id="uxz9ak"
getKeycloakInstance().token
```

---

## 🧪 Probar endpoint con token

Desde otra terminal:

```bash id="m2r7pn"
curl -H "Authorization: Bearer TU_ACCESS_TOKEN" \
http://localhost:3000/protected
```

Reemplazar `TU_ACCESS_TOKEN` por el token real.

---

## ✅ Resultado esperado

Debe responder algo similar a:

```json id="o2wq7x"
{
  "message": "Protected resource",
  "user": { ...claims del token... }
}
```

---

## 🧪 Probar token inválido

Modificar un carácter del token y ejecutar:

```bash id="v8q3lp"
curl -H "Authorization: Bearer TOKEN_MODIFICADO" \
http://localhost:3000/protected
```

Resultado esperado:

```json id="r5mt9z"
{ "error": "Invalid token" }
```

---

## 🧠 Qué estamos validando

* La firma RS256 es verificada correctamente.
* La clave pública se obtiene dinámicamente desde JWKS.
* Tokens manipulados son rechazados.
* El backend confía únicamente en tokens válidos emitidos por Keycloak.
