# Lab 01 — OpenLDAP

## Paso 02 — Levantar el contenedor LDAP

---

## 🎯 Objetivo

Arrancar el servicio OpenLDAP y verificar que está funcionando correctamente.

---

## 📍 Ubicación

Desde la raíz del proyecto:

```
infra/
```

---

## ▶️ Levantar contenedores

Ejecutar:

```bash id="n4y2zt"
docker compose up -d
```

---

## 🔎 Verificar estado del contenedor

Ejecutar:

```bash id="c7lx9r"
docker ps
```

Debe aparecer un contenedor llamado:

```
openldap
```

Con puerto:

```
0.0.0.0:389->389/tcp
```

---

## 📋 Ver logs

Para comprobar que el servicio arrancó correctamente:

```bash id="m3t8qp"
docker logs openldap
```

No debe haber errores críticos.

---

## 🧠 Qué estamos validando

* El servicio LDAP está activo.
* El puerto 389 está expuesto.
* El contenedor está funcionando correctamente.

En el siguiente paso validaremos conexión al directorio LDAP.
