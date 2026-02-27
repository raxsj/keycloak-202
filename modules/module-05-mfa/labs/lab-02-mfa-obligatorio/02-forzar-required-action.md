# Lab 02 — MFA Obligatorio

## Paso 02 — Forzar Required Action para OTP

---

## 🎯 Objetivo

Obligar a los usuarios a configurar TOTP en su próximo inicio de sesión.

---

## 📍 Acceder a usuario

Ir a:

```
Users
```

Seleccionar un usuario, por ejemplo:

```
user1
```

---

## 🔧 Asignar acción requerida

Ir a la pestaña:

```
Required Actions
```

Añadir:

```
Configure OTP
```

Guardar cambios.

---

## 🧪 Cerrar sesión

Cerrar sesión completamente desde la aplicación o desde:

```
http://localhost:8080/realms/training/account
```

---

## 🧪 Iniciar sesión nuevamente

Intentar iniciar sesión con el usuario configurado.

---

## 🔎 Comportamiento esperado

Después de introducir usuario y contraseña:

* No se accederá directamente a la aplicación.
* Se mostrará pantalla para configurar OTP.
* Se pedirá escanear un código QR.
* Se deberá introducir código de 6 dígitos.

---

## 📱 Completar registro

1. Abrir aplicación autenticadora.
2. Escanear código QR.
3. Introducir código generado.
4. Confirmar.

---

## 🧠 Qué estamos validando

* Required Action funciona correctamente.
* El usuario no puede continuar sin configurar TOTP.
* El segundo factor queda asociado a la cuenta.
* El flujo personalizado soporta MFA.
