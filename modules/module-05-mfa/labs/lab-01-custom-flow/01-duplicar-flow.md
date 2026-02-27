# Lab 01 — Custom Authentication Flow

## Paso 01 — Duplicar el flujo de autenticación

---

## 🎯 Objetivo

Crear un flujo de autenticación personalizado a partir del flujo `browser` por defecto.

---

## 🧠 Contexto

Keycloak permite:

* Definir flujos de autenticación.
* Añadir, quitar o reordenar ejecuciones.
* Crear flujos personalizados sin modificar el original.

Nunca se debe modificar directamente el flujo `browser` por defecto.

---

## 📍 Acceder a Flows

Ir a:

```
Authentication → Flows
```

---

## 📋 Localizar flujo base

Buscar:

```
browser
```

Este es el flujo utilizado por defecto en login web.

---

## ➕ Duplicar flujo

1. Seleccionar `browser`.
2. Pulsar **Duplicate**.
3. Introducir nombre:

   browser-custom

Guardar.

---

## 🔎 Verificación

En la lista debe aparecer:

```
browser-custom
```

Debe contener la misma estructura que el flujo original.

---

## 🧠 Qué hemos hecho

* Creamos un flujo independiente.
* Evitamos modificar el flujo por defecto.
* Estamos listos para personalizar ejecuciones en el siguiente paso.
