# Lab 02 — SSL

## Paso 03 — Validar canal seguro HTTPS

---

## 🎯 Objetivo

Comprobar que la comunicación entre el navegador y NGINX se realiza mediante HTTPS y que Keycloak genera URLs coherentes.

---

## 🌐 Acceder por HTTPS

Abrir:

```
https://localhost:8443
```

Aceptar advertencia de certificado autofirmado.

---

## 🔎 Verificar protocolo

En el navegador:

* Debe aparecer candado (aunque no confiable).
* La URL debe comenzar por:

  https://

---

## 🧪 Validar redirección automática

Intentar acceder por:

```
http://localhost:8081
```

Debe redirigir automáticamente a:

```
https://localhost:8443
```

---

## 🧪 Verificar issuer

Abrir:

```
https://localhost:8443/realms/training/.well-known/openid-configuration
```

Revisar el campo:

```
issuer
```

Debe comenzar por:

```
https://localhost:8443
```

---

## 🧪 Validar con curl

Ejecutar:

```bash id="f7mpz2"
curl -k https://localhost:8443
```

La opción `-k` permite ignorar certificado autofirmado.

Debe devolver HTML de Keycloak.

---

## 🧠 Qué estamos validando

* El tráfico externo viaja cifrado.
* NGINX termina TLS correctamente.
* Keycloak construye URLs HTTPS.
* El entorno simula arquitectura productiva con reverse proxy + TLS.

---

## 🧠 Estado del laboratorio

* Reverse proxy configurado.
* HTTPS activo.
* Headers correctamente reenviados.
* Entorno preparado para aplicar hardening en el siguiente laboratorio.
