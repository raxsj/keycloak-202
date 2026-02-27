# Lab 03 — Proteger Endpoints

## Paso 02 — Validar scopes en el backend

---

## 🎯 Objetivo

Restringir acceso a un endpoint en función de los **scopes** incluidos en el `access_token`.

---

## 🧠 Contexto

Los scopes aparecen en el claim:

```
scope
```

Ejemplo típico:

```json
{
  "scope": "openid profile email api.read api.write"
}
```

El claim `scope` es un string separado por espacios.

---

## 📍 Ubicación

Dentro de:

```
apps/api-node
```

---

## ✍️ Crear middleware de validación de scope

Editar:

```
auth.middleware.js
```

Añadir función:

```javascript
function requireScope(requiredScope) {
  return (req, res, next) => {
    const scopeClaim = req.user?.scope;

    if (!scopeClaim) {
      return res.status(403).json({ error: 'No scopes present in token' });
    }

    const scopes = scopeClaim.split(' ');

    if (!scopes.includes(requiredScope)) {
      return res.status(403).json({ error: 'Insufficient scope' });
    }

    next();
  };
}
```

Actualizar exportación:

```javascript
module.exports = { authenticateToken, requireRole, requireScope };
```

---

## 📍 Aplicar a nuevo endpoint

Editar:

```
index.js
```

Importar:

```javascript
const { authenticateToken, requireRole, requireScope } = require('./auth.middleware');
```

Añadir nuevo endpoint:

```javascript
app.get(
  '/scoped',
  authenticateToken,
  requireScope('api.read'),
  (req, res) => {
    res.json({
      message: 'Scoped resource (api.read required)',
      user: req.user
    });
  }
);
```

---

## 🧠 Estado actual

* El backend valida firma JWT.
* Puede restringir por rol.
* Puede restringir por scope.
* La autorización es ahora granular y basada en claims del token.
