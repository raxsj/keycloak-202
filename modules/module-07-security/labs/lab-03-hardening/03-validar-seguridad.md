# Lab 03 — Hardening

## Paso 03 — Validar configuración de seguridad

---

## 🎯 Objetivo

Comprobar que las medidas de hardening aplicadas funcionan correctamente y no rompen el flujo normal de autenticación.

---

## 🧪 Validar SPA

1. Acceder a:

   [https://localhost:8443](https://localhost:8443)

2. Iniciar sesión normalmente.

3. Navegar a rutas protegidas.

Resultado esperado:

* Login funciona.
* No hay errores de redirect.
* El flujo Authorization Code con PKCE sigue operativo.

---

## 🧪 Probar flujo deshabilitado (Direct Access Grants)

Intentar obtener token con password grant:

```bash id="x3d9wk"
curl -X POST \
  https://localhost:8443/realms/training/protocol/openid-connect/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=password" \
  -d "client_id=spa-client" \
  -d "username=user1" \
  -d "password=password" \
  -k
```

Resultado esperado:

```
error: unauthorized_client
```

---

## 🧪 Probar redirect URI inválida

Intentar construir URL de autorización con redirect no permitido:

```
https://localhost:8443/realms/training/protocol/openid-connect/auth?client_id=spa-client&response_type=code&redirect_uri=http://malicious-site.com
```

Resultado esperado:

* Error de redirect URI.
* Keycloak rechaza solicitud.

---

## 🧠 Validar expiración corta

1. Esperar a que el token expire.
2. Observar comportamiento de refresh automático.

Resultado esperado:

* Token se renueva correctamente.
* Si no se renueva, se fuerza relogin.

---

## 🧠 Qué estamos confirmando

* Solo flujos permitidos funcionan.
* Redirect URIs restringidas se aplican.
* Password grant está deshabilitado.
* Tokens tienen vida limitada.
* El entorno cumple principios básicos de hardening.

---

## 🧠 Estado del módulo

* Reverse proxy con HTTPS.
* Headers correctamente configurados.
* Tokens con expiración reducida.
* Clientes bajo principio de mínimo privilegio.
* Arquitectura preparada para entornos empresariales.
