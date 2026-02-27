# Lab 01 — Custom Authentication Flow

## Paso 02 — Modificar ejecuciones del flujo

---

## 🎯 Objetivo

Modificar el flujo `browser-custom` para añadir o cambiar requisitos de autenticación.

---

## 📍 Acceder al flujo

Ir a:

```
Authentication → Flows → browser-custom
```

---

## 🧠 Estructura del flujo

Verás ejecuciones como:

* Cookie
* Identity Provider Redirector
* Username Password Form

Cada ejecución puede tener un requisito:

* REQUIRED
* ALTERNATIVE
* DISABLED
* CONDITIONAL

---

## 🔧 Modificar requisito

Cambiar el requisito de:

```
Username Password Form → REQUIRED
```

(Si ya está en REQUIRED, mantenerlo)

---

## ➕ Añadir ejecución adicional (ejemplo)

Dentro del subflow:

```
Forms
```

1. Pulsar **Add execution**

2. Seleccionar:

   OTP Form

3. Añadirla.

4. Cambiar su requisito a:

   OPTIONAL

---

## 💾 Guardar cambios

Asegurarse de que:

* El flujo no tiene errores de configuración.
* No existen ejecuciones marcadas incorrectamente.

---

## 🧠 Qué estamos haciendo

* Personalizamos el comportamiento del login.
* Introducimos un segundo factor opcional.
* Preparamos el flujo para forzar MFA en el siguiente laboratorio.
