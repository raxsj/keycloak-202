# Lab 03 — Hardening

## Paso 01 — Configurar expiraciones seguras de tokens

---

## 🎯 Objetivo

Ajustar la política de expiración de tokens para reducir riesgos en caso de robo o uso indebido.

---

## 🧠 Contexto

En entornos productivos:

* Access tokens deben ser de corta duración.
* Refresh tokens deben tener rotación o caducidad limitada.
* Las sesiones no deben ser indefinidas.

Reducir tiempos limita el impacto de un token comprometido.

---

## 📍 Acceder a configuración de tokens

Ir a:

```
Realm Settings → Tokens
```

---

## 🔧 Ajustar valores recomendados

Modificar:

* Access Token Lifespan → 5 minutes
* SSO Session Idle → 15 minutes
* SSO Session Max → 8 hours
* Client Session Idle → 10 minutes

Guardar cambios.

---

## 🔎 Validar expiración

1. Iniciar sesión.
2. Observar `exp` en el token desde Angular:

```javascript
getKeycloakInstance().tokenParsed.exp
```

3. Confirmar que el tiempo restante es reducido.

---

## 🧠 Impacto de estos cambios

* Tokens expiran rápidamente.
* Refresh automático se vuelve crítico.
* Reduce superficie de ataque.
* Simula configuración realista de producción.

---

## 🧠 Estado actual

* La política de tokens está endurecida.
* La seguridad mejora frente a robo de tokens.
* En el siguiente paso aplicaremos restricciones adicionales a clientes.
