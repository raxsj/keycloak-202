# Lab 03 — Hardening

## Paso 02 — Restringir configuración de clientes

---

## 🎯 Objetivo

Reducir superficie de ataque limitando flujos y permisos innecesarios en los clientes.

---

## 🧠 Contexto

Errores comunes en producción:

* Dejar activados flujos no utilizados.
* Permitir Direct Access Grants sin necesidad.
* Permitir múltiples redirect URIs amplias (`*`).

El hardening consiste en permitir solo lo estrictamente necesario.

---

## 📍 Revisar cliente SPA

Ir a:

```
Clients → spa-client
```

---

## 🔧 Ajustar flujos

En sección **Capability config**:

* Standard Flow → ON
* Direct Access Grants → OFF
* Implicit Flow → OFF
* Service Accounts → OFF

Guardar.

---

## 🔧 Restringir Redirect URIs

En sección **Access Settings**:

Eliminar:

```
*
```

Dejar únicamente:

```
https://localhost:8443/*
http://localhost:4200/*  (solo si se usa en dev)
```

Evitar comodines amplios en producción.

---

## 📍 Revisar cliente backend-service

Ir a:

```
Clients → backend-service
```

Confirmar:

* Client authentication → ON
* Standard Flow → OFF
* Direct Access Grants → OFF
* Service Accounts → ON

---

## 🧠 Qué estamos endureciendo

* Eliminamos flujos innecesarios.
* Reducimos vectores de ataque.
* Restringimos redirect URIs.
* Evitamos grant types no requeridos.

---

## 🧠 Estado actual

* Clientes configurados bajo principio de mínimo privilegio.
* Flujos innecesarios desactivados.
* Reducción de superficie de exposición.
* En el siguiente paso validaremos la configuración de seguridad completa.
