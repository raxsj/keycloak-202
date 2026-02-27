# Lab 02 — Validación JWT

## Paso 02 — Crear middleware de validación

---

## 🎯 Objetivo

Crear un middleware que valide el `access_token` enviado en el header `Authorization`.

---

## 📍 Ubicación

Dentro de:

```
apps/api-node
```

---

## 📁 Crear archivo middleware

Crear:

```
auth.middleware.js
```

Contenido:

```javascript id="kz7q2p"
const jwt = require('jsonwebtoken');
const jwksClient = require('jwks-rsa');

const client = jwksClient({
  jwksUri: 'http://localhost:8080/realms/training/protocol/openid-connect/certs'
});

function getKey(header, callback) {
  client.getSigningKey(header.kid, function (err, key) {
    const signingKey = key.getPublicKey();
    callback(null, signingKey);
  });
}

function authenticateToken(req, res, next) {
  const authHeader = req.headers['authorization'];

  if (!authHeader) {
    return res.status(401).json({ error: 'Missing Authorization header' });
  }

  const token = authHeader.split(' ')[1];

  jwt.verify(token, getKey, {
    algorithms: ['RS256'],
    issuer: 'http://localhost:8080/realms/training'
  }, (err, decoded) => {
    if (err) {
      return res.status(403).json({ error: 'Invalid token' });
    }

    req.user = decoded;
    next();
  });
}

module.exports = { authenticateToken };
```

---

## 📍 Integrar middleware en servidor

Abrir:

```
index.js
```

Importar el middleware:

```javascript id="k2j3mn"
const { authenticateToken } = require('./auth.middleware');
```

Modificar el endpoint `/protected`:

```javascript id="z4m9lx"
app.get('/protected', authenticateToken, (req, res) => {
  res.json({
    message: 'Protected resource',
    user: req.user
  });
});
```

---

## 🧠 Estado actual

* El endpoint `/protected` ahora exige un token válido.
* El backend valida:

  * Firma (RS256)
  * Issuer
  * Clave pública vía JWKS
* En el siguiente paso probaremos la validación con un token real.
