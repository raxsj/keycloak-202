# Lab 01 — Crear API Node

## Paso 02 — Crear servidor Express

---

## 🎯 Objetivo

Instalar Express y crear un servidor HTTP básico que escuche en el puerto 3000.

---

## 📍 Ubicación

Desde:

```
apps/api-node
```

---

## 📦 Instalar Express

Ejecutar:

```bash id="1m3x9q"
npm install express
```

---

## ✍️ Implementar servidor

Abrir:

```
index.js
```

Reemplazar su contenido por:

```javascript id="v8k2zp"
const express = require('express');

const app = express();
const PORT = 3000;

app.use(express.json());

app.get('/', (req, res) => {
  res.json({ message: 'API is running' });
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

---

## ▶️ Ejecutar servidor

```bash id="t2q9hj"
node index.js
```

---

## 🌐 Validar funcionamiento

Abrir en navegador:

```
http://localhost:3000
```

Debe responder:

```json
{ "message": "API is running" }
```

---

## 🧠 Estado actual

* Backend Node funcionando.
* Servidor Express escuchando en puerto 3000.
* Endpoint básico disponible.
* Listo para añadir endpoints protegidos en el siguiente paso.
