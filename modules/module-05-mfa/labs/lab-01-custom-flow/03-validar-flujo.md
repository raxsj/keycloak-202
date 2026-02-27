# Lab 01 — Custom Authentication Flow

## Paso 03 — Activar y validar el flujo personalizado

---

## 🎯 Objetivo

Asignar el flujo `browser-custom` como flujo activo del realm y comprobar su funcionamiento.

---

## 📍 Asignar flujo al realm

Ir a:

```
Authentication → Bindings
```

En el campo:

```
Browser Flow
```

Seleccionar:

```
browser-custom
```

Guardar cambios.

---

## 🧪 Probar autenticación

1. Cerrar sesión si estás autenticado.
2. Acceder a la aplicación Angular o directamente a:

   [http://localhost:8080/realms/training/account](http://localhost:8080/realms/training/account)

---

## 🔎 Comportamiento esperado

* El login utiliza ahora el flujo `browser-custom`.
* Si añadiste OTP como OPTIONAL, no se forzará todavía.
* El comportamiento base debe seguir funcionando correctamente.

---

## 🧪 Verificar errores

Si el flujo estuviera mal configurado:

* Podría aparecer error de autenticación.
* Podría bloquear el login.

En ese caso:

```
Authentication → Bindings
```

Volver temporalmente al flujo `browser`.

---

## 🧠 Qué estamos validando

* El realm puede usar flujos personalizados.
* El flujo duplicado funciona correctamente.
* La personalización no rompe el proceso de login.
* El sistema está listo para forzar MFA en el siguiente laboratorio.
