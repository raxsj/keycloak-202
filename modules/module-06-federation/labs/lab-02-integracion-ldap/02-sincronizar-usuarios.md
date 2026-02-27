# Lab 02 — Integración LDAP

## Paso 02 — Sincronizar usuarios desde LDAP

---

## 🎯 Objetivo

Importar usuarios del servidor OpenLDAP al realm `training`.

---

## 🧠 Contexto

Con:

```
Import Users = ON
```

Keycloak:

* Copia usuarios LDAP al almacenamiento interno.
* Mantiene referencia al origen LDAP.
* Permite autenticación delegada.

---

## 📍 Crear usuario de prueba en LDAP

Entrar al contenedor:

```bash
docker exec -it openldap bash
```

Crear archivo:

```
/tmp/user.ldif
```

Contenido:

```
dn: uid=john,dc=training,dc=local
objectClass: inetOrgPerson
objectClass: organizationalPerson
objectClass: person
objectClass: top
cn: John Doe
sn: Doe
uid: john
mail: john@training.local
userPassword: password
```

Importar usuario:

```bash
ldapadd -x -D "cn=admin,dc=training,dc=local" -w admin -f /tmp/user.ldif
```

Salir del contenedor.

---

## 📍 Sincronizar en Keycloak

Ir a:

```
User Federation → ldap
```

Pulsar:

```
Synchronize all users
```

---

## 🔎 Verificar importación

Ir a:

```
Users
```

Debe aparecer:

```
john
```

Con origen:

```
LDAP
```

---

## 🧠 Qué estamos validando

* Keycloak puede importar usuarios LDAP.
* La sincronización funciona correctamente.
* El usuario existe tanto en LDAP como en Keycloak.
* El siguiente paso validará autenticación con credenciales LDAP.
