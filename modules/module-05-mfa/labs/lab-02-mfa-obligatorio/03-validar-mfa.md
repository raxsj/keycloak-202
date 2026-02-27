# Lab 02 — MFA Obligatorio

## Paso 03 — Validar autenticación con MFA

---

## 🎯 Objetivo

Verificar que el login ahora requiere segundo factor y que la autenticación funciona correctamente con TOTP.

---

## 🧪 Escenario 1 — Usuario con OTP configurado

1. Cerrar sesión completamente.

2. Acceder a la aplicación Angular o a:

   [http://localhost:8080/realms/training/account](http://localhost:8080/realms/training/account)

3. Introducir usuario y contraseña.

---

## 🔎 Comportamiento esperado

Después de validar usuario y contraseña:

* Aparece pantalla solicitando código OTP.
* No se permite continuar sin introducir el código.
* Tras introducir código correcto, se completa el login.

---

## 🧪 Escenario 2 — Código incorrecto

1. Introducir código erróneo.
2. Validar.

Resultado esperado:

* Error de autenticación.
* No se concede acceso.

---

## 🧪 Escenario 3 — Usuario sin OTP configurado

Si el usuario no tiene Required Action activa:

* No se solicitará segundo factor.
* El login continuará normalmente.

---

## 🧠 Validación técnica

En el flujo de autenticación:

* Se ejecuta `Username Password Form`.
* Se ejecuta `OTP Form`.
* El flujo no permite continuar si el OTP falla.

---

## 🧠 Qué estamos confirmando

* El segundo factor está activo.
* La autenticación es multifactor.
* El flujo personalizado soporta MFA correctamente.
* El realm ahora aplica seguridad reforzada en login.
