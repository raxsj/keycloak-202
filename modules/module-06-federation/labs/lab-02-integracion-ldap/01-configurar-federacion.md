# Lab 02 — Integración LDAP

## Paso 01 — Configurar User Federation en Keycloak

---

## 🎯 Objetivo

Configurar Keycloak para que utilice el servidor OpenLDAP como fuente externa de usuarios.

---

## 📍 Acceder a configuración

Ir a:

```
User Federation
```

Seleccionar:

```
Add provider → ldap
```

---

## 🔧 Configuración básica

Completar los campos principales:

* Vendor → Other
* Connection URL → ldap://openldap:389
* Bind DN → cn=admin,dc=training,dc=local
* Bind Credential → admin
* Users DN → dc=training,dc=local

---

## ⚙️ Ajustes recomendados

* Edit Mode → READ_ONLY
* Import Users → ON
* Sync Registrations → OFF
* Trust Email → OFF

Guardar configuración.

---

## 🔎 Probar conexión

Pulsar botón:

```
Test connection
```

Debe mostrar:

```
Success
```

Luego:

```
Test authentication
```

Debe mostrar:

```
Success
```

---

## 🧠 Qué hemos configurado

* Keycloak puede conectarse al LDAP.
* Se autentica usando el usuario admin.
* Está preparado para sincronizar usuarios.
* El siguiente paso consistirá en importar o sincronizar usuarios desde LDAP.
