# Lab 03 — Identity Brokering

## Paso 03 — Validar autenticación mediante Broker

---

## 🎯 Objetivo

Comprobar que un usuario del realm `partner` puede autenticarse en el realm `training` mediante Identity Brokering.

---

## 🧪 Iniciar flujo de login

Acceder a:

```
http://localhost:8080/realms/training/account
```

En la pantalla de login debe aparecer:

```
Partner Login
```

---

## 🔄 Autenticarse en realm externo

1. Pulsar **Partner Login**.

2. El navegador redirige a:

   realm partner

3. Introducir:

   Username: partner-user
   Password: password

---

## 🔁 Redirección de vuelta

Tras autenticación correcta:

* El navegador vuelve al realm `training`.
* Se crea automáticamente un usuario federado.
* Se concede acceso a la aplicación.

---

## 📍 Verificar usuario creado

Ir a:

```
training → Users
```

Debe existir un nuevo usuario con:

* Federation Link → partner-idp
* Username similar a partner-user

---

## 🧠 Qué estamos validando

* El flujo OIDC entre realms funciona.
* El realm `training` actúa como Service Provider.
* El realm `partner` actúa como Identity Provider.
* Los usuarios externos pueden autenticarse sin existir previamente en el realm consumidor.
* Se crea enlace federado entre identidades.

---

## 🧠 Resultado del módulo

* LDAP Federation configurada.
* Identity Brokering configurado.
* Realm soporta autenticación híbrida.
* Arquitectura preparada para escenarios enterprise multi-sistema.
