# Lab 01 — NGINX Reverse Proxy

## Paso 03 — Validar headers X-Forwarded

---

## 🎯 Objetivo

Comprobar que los headers reenviados por NGINX llegan correctamente a Keycloak.

---

## 🧠 Contexto

Cuando Keycloak está detrás de proxy:

* Usa `X-Forwarded-Proto` para construir URLs.
* Usa `Host` para issuer y redirecciones.
* Usa `X-Forwarded-For` para IP real del cliente.

Si estos headers no llegan correctamente:

* Puede generarse issuer incorrecto.
* Puede fallar el login.
* Pueden generarse bucles de redirección.

---

## 🧪 Verificar issuer vía proxy

Abrir:

```
http://localhost:8081/realms/training/.well-known/openid-configuration
```

Revisar el campo:

```
issuer
```

Debe usar:

```
http://localhost:8081/realms/training
```

No debe mostrar:

```
http://keycloak:8080
```

---

## 🧪 Validar redirecciones

Intentar iniciar login desde:

```
http://localhost:8081
```

Verificar que:

* La URL de login usa el puerto 8081.
* No redirige internamente a 8080.
* No aparecen errores de hostname.

---

## 🧪 Validar logs del contenedor

Ejecutar:

```bash id="vhc8rm"
docker logs keycloak
```

No deben aparecer advertencias relacionadas con proxy o hostname.

---

## 🧠 Qué estamos confirmando

* Los headers `X-Forwarded-*` se transmiten correctamente.
* Keycloak respeta el host público.
* El issuer es coherente.
* La arquitectura reverse proxy está correctamente configurada.

El entorno está preparado para añadir HTTPS en el siguiente laboratorio.
