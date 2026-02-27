# Lab 03 — Proteger Endpoints

## Paso 01 — Validar roles en el backend

---

## 🎯 Objetivo

Restringir el acceso a un endpoint en función de los **roles** incluidos en el token JWT.

---

## 🧠 Contexto

Keycloak incluye los roles en el claim:

```
realm_access.roles
```

Ejemplo dentro del token:

```json
{
  "realm_access": {
    "roles": ["user", "admin"]
  }
}
```

Podemos usar esta información para aplicar autorización en el backend.

---

## 📍 Ubicación

Dentro de:

```
apps/api-node
```

---

## ✍️ Crear middleware de autorización por rol

Editar:

```
auth.middleware.js
```

Añadir función:

```javascript id="g7p9ls"
function requireRole(role) {
  return (req, res, next) => {
    const roles = req.user?.realm_access?.roles || [];

    if (!roles.includes(role)) {
      return res.status(403).json({ error: 'Insufficient role' });
    }

    next();
  };
}
```

Actualizar exportación:

```javascript id="j9k3pt"
module.exports = { authenticateToken, requireRole };
```

---

## 📍 Aplicar middleware al endpoint

Editar:

```
index.js
```

Importar:

```javascript id="m4t8rz"
const { authenticateToken, requireRole } = require('./auth.middleware');
```

Modificar `/protected`:

```javascript id="k2z6op"
app.get(
  '/protected',
  authenticateToken,
  requireRole('admin'),
  (req, res) => {
    res.json({
      message: 'Protected resource (admin only)',
      user: req.user
    });
  }
);
```

---

## 🧠 Estado actual

* El backend valida el JWT.
* Además verifica que el usuario tenga el rol `admin`.
* Si no lo tiene, devuelve 403.
* La autorización ahora depende del contenido del token.
