# Lab 01 — OpenLDAP

## Paso 03 — Validar conexión al LDAP

---

## 🎯 Objetivo

Comprobar que el servidor OpenLDAP está accesible y responde correctamente.

---

## 📍 Opción 1 — Probar desde contenedor (recomendado)

Entrar al contenedor:

```bash
docker exec -it openldap bash
```

Dentro del contenedor ejecutar:

```bash
ldapsearch -x -H ldap://localhost \
-D "cn=admin,dc=training,dc=local" \
-w admin \
-b "dc=training,dc=local"
```

---

## 📍 Opción 2 — Instalar cliente ldapsearch (si no existe)

En Codespace:

```bash
sudo apt update
sudo apt install ldap-utils
```

Luego ejecutar:

```bash
ldapsearch -x -H ldap://localhost:389 \
-D "cn=admin,dc=training,dc=local" \
-w admin \
-b "dc=training,dc=local"
```

---

## 🔎 Resultado esperado

Debe mostrarse una respuesta similar a:

```
dn: dc=training,dc=local
objectClass: top
objectClass: dcObject
objectClass: organization
o: Training Org
dc: training
```

---

## 🧠 Qué estamos validando

* El servidor LDAP acepta conexiones.
* Las credenciales de administrador funcionan.
* El DN base es correcto.
* El entorno está listo para federar usuarios desde Keycloak en el siguiente laboratorio.
