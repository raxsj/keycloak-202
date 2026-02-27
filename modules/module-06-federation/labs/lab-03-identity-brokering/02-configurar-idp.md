# Lab 03 — Identity Brokering

## Paso 02 — Configurar realm partner como Identity Provider

---

## 🎯 Objetivo

Configurar el realm `training` para que permita autenticación delegada al realm `partner`.

---

## 📍 Cambiar al realm consumidor

Seleccionar:

```
training
```

---

## 📍 Añadir Identity Provider

Ir a:

```
Identity Providers
```

Seleccionar:

```
Add provider → Keycloak OpenID Connect
```

---

## 🔧 Configuración básica

Completar:

* Alias → partner-idp
* Display Name → Partner Login
* Authorization URL →
  [http://localhost:8080/realms/partner/protocol/openid-connect/auth](http://localhost:8080/realms/partner/protocol/openid-connect/auth)
* Token URL →
  [http://localhost:8080/realms/partner/protocol/openid-connect/token](http://localhost:8080/realms/partner/protocol/openid-connect/token)
* Logout URL →
  [http://localhost:8080/realms/partner/protocol/openid-connect/logout](http://localhost:8080/realms/partner/protocol/openid-connect/logout)
* User Info URL →
  [http://localhost:8080/realms/partner/protocol/openid-connect/userinfo](http://localhost:8080/realms/partner/protocol/openid-connect/userinfo)
* Client ID → training-broker
* Client Secret → (se configurará después)

Guardar.

---

## 📍 Crear cliente en realm partner

Cambiar a:

```
partner
```

Ir a:

```
Clients → Create client
```

Configurar:

* Client type → OpenID Connect
* Client ID → training-broker

Next:

* Client authentication → ON
* Standard flow → ON

Guardar.

Ir a:

```
Credentials
```

Copiar:

```
Client Secret
```

---

## 📍 Completar configuración en training

Volver a:

```
training → Identity Providers → partner-idp
```

Pegar:

```
Client Secret
```

Guardar.

---

## 🔎 Verificación

En la pantalla de login del realm `training` debe aparecer un nuevo botón:

```
Partner Login
```

---

## 🧠 Estado actual

* Realm `training` delega autenticación en `partner`.
* Se ha configurado OIDC como broker.
* Listo para validar autenticación cruzada en el siguiente paso.
