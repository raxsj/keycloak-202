# Lab 04 — Service Account

## Paso 01 — Crear cliente confidencial para service-to-service

---

## 🎯 Objetivo

Crear un cliente **confidencial** en Keycloak que permita autenticación sin usuario mediante `Client Credentials Flow`.

---

## 🧠 Contexto

El flujo **Client Credentials** se usa cuando:

* No existe usuario interactivo.
* Un servicio necesita autenticarse contra otro.
* Se utiliza `client_id + client_secret`.

---

## 📍 Ir a Keycloak

Acceder a:

```
http://localhost:8080
```

Seleccionar el realm:

```
training
```

---

## ➕ Crear nuevo cliente

1. Ir a **Clients**
2. Pulsar **Create client**
3. Configurar:

   Client type: OpenID Connect
   Client ID: backend-service

Pulsar **Next**

---

## ⚙️ Configuración

En la siguiente pantalla:

* Client authentication → ON
* Standard flow → OFF
* Direct access grants → OFF
* Service accounts roles → ON

Guardar.

---

## 🔐 Obtener credenciales

Ir a:

```
Clients → backend-service → Credentials
```

Copiar:

```
Client secret
```

---

## 🧠 Qué hemos configurado

* Cliente confidencial.
* Permite autenticación sin usuario.
* Utiliza Client Credentials Flow.
* Generará tokens con identidad del cliente.

En el siguiente paso utilizaremos estas credenciales para consumir la API protegida.
