# Lab 02 — Integración LDAP

## Paso 03 — Validar autenticación con usuario LDAP

---

## 🎯 Objetivo

Comprobar que un usuario almacenado en OpenLDAP puede autenticarse en Keycloak.

---

## 📍 Verificar configuración

En:

```
User Federation → ldap
```

Confirmar:

* Edit Mode → READ_ONLY
* Import Users → ON
* Sync Registrations → OFF

Guardar si fuera necesario.

---

## 🧪 Cerrar sesión

Cerrar sesión completamente desde la aplicación o desde:

```
http://localhost:8080/realms/training/account
```

---

## 🧪 Intentar login con usuario LDAP

En la pantalla de login introducir:

```
Username: john
Password: password
```

---

## 🔎 Resultado esperado

* Login exitoso.
* Redirección a la aplicación Angular.
* En la lista de usuarios, el usuario aparece con origen LDAP.

---

## 🧪 Probar contraseña incorrecta

Introducir contraseña errónea.

Resultado esperado:

* Error de autenticación.
* No se concede acceso.

---

## 🧠 Qué estamos validando

* Keycloak delega autenticación en LDAP.
* La contraseña no se valida internamente en Keycloak.
* El usuario LDAP puede integrarse en flujos existentes (MFA, roles, etc.).
* El realm soporta federación externa correctamente.
