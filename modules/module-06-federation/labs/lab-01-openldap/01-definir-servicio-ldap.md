# Lab 01 — OpenLDAP

## Paso 01 — Definir servicio LDAP en Docker Compose

---

## 🎯 Objetivo

Añadir un servicio OpenLDAP al entorno Docker para simular un directorio corporativo externo.

---

## 🧠 Contexto

User Federation permite que Keycloak:

* No almacene usuarios localmente.
* Delegue autenticación en un LDAP externo.
* Sincronice usuarios desde sistemas corporativos.

En este laboratorio levantaremos un LDAP propio en Docker.

---

## 📍 Ubicación

Editar:

```
infra/docker-compose.yml
```

---

## ➕ Añadir servicio OpenLDAP

Dentro de `services:` añadir:

```yaml id="xq7plm"
  openldap:
    image: osixia/openldap:1.5.0
    container_name: openldap
    environment:
      LDAP_ORGANISATION: "Training Org"
      LDAP_DOMAIN: "training.local"
      LDAP_ADMIN_PASSWORD: admin
    ports:
      - "389:389"
    restart: always
```

---

## 🧠 Qué estamos configurando

* Dominio LDAP: training.local

* DN base: dc=training,dc=local

* Usuario admin:

  ```
  cn=admin,dc=training,dc=local
  ```

* Contraseña:

  ```
  admin
  ```

---

## 💾 Guardar cambios

Asegurarse de que la indentación YAML es correcta.

---

## 🧠 Estado actual

* Servicio LDAP definido.
* Integrado en el entorno Docker.
* En el siguiente paso levantaremos el contenedor.
