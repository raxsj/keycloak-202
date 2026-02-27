# Lab 03 — Theme Personalizado

## Paso 03 — Validar cambios del Theme

---

## 🎯 Objetivo

Comprobar que el theme personalizado se aplica correctamente y entender cómo forzar recarga en modo desarrollo.

---

## 🧪 Probar pantalla de login

1. Cerrar sesión completamente.
2. Acceder a:

   [http://localhost:8080/realms/training/account](http://localhost:8080/realms/training/account)

---

## 🔎 Verificaciones visuales

Comprobar que:

* El fondo tiene color personalizado.

* El encabezado muestra:

  Keycloak Training Portal

* La tarjeta de login tiene bordes redondeados.

* El CSS definido se aplica correctamente.

---

## 🔄 Forzar recarga de cambios

Si realizas modificaciones en CSS o FTL:

1. Reiniciar contenedor:

```bash id="xq9htp"
docker compose restart
```

2. Limpiar caché del navegador (Ctrl + Shift + R).

---

## 🧪 Validar que realmente es tu theme

Cambiar temporalmente el color de fondo en:

```
styles.css
```

Por ejemplo:

```css id="r3jqsz"
body {
  background-color: red;
}
```

Reiniciar y comprobar que el cambio es visible.

---

## 🧠 Qué estamos validando

* El theme está correctamente montado en el contenedor.
* Keycloak utiliza el theme configurado en el realm.
* Las plantillas FTL pueden sobreescribirse.
* El branding puede adaptarse a entornos empresariales.

---

## 🧠 Estado del módulo

* Se han creado flujos personalizados.
* Se ha activado MFA obligatorio.
* Se ha personalizado la interfaz de login.
* El realm está configurado con autenticación avanzada y branding propio.
