# Lab 01 — Crear API Node

## Paso 03 — Crear endpoint protegido simulado

---

## 🎯 Objetivo

Crear un endpoint adicional que represente un recurso protegido, aunque todavía no valide JWT.

---

## 📍 Ubicación

Dentro de:

```
apps/api-node
```

---

## ✍️ Editar servidor

Abrir:

```
index.js
```

Añadir debajo del endpoint `/`:

```javascript id="3x7kdu"
app.get('/protected', (req, res) => {
  res.json({
    message: 'This is a protected resource (no validation yet)',
    timestamp: new Date().toISOString()
  });
});
```

El archivo completo debería quedar similar a:

```javascript id="6m2pqo"
const express = require('express');

const app = express();
const PORT = 3000;

app.use(express.json());

app.get('/', (req, res) => {
  res.json({ message: 'API is running' });
});

app.get('/protected', (req, res) => {
  res.json({
    message: 'This is a protected resource (no validation yet)',
    timestamp: new Date().toISOString()
  });
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

---

## ▶️ Reiniciar servidor

Si está ejecutándose, detenerlo y volver a lanzar:

```bash
node index.js
```

---

## 🌐 Validar endpoint

Abrir en navegador:

```
http://localhost:3000/protected
```

Debe devolver un JSON con mensaje y timestamp.

---

## 🧠 Estado actual

* API Node funcionando.
* Endpoint `/protected` creado.
* Aún no existe validación de tokens.
* Preparado para implementar validación JWT en el siguiente laboratorio.
