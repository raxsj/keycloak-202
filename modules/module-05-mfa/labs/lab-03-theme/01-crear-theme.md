# Lab 03 — Theme Personalizado

## Paso 01 — Crear estructura base del Theme

---

## 🎯 Objetivo

Crear un theme personalizado para modificar la apariencia de la pantalla de login.

---

## 🧠 Contexto

Keycloak permite personalizar:

* Login
* Account
* Email
* Admin console

Los themes se cargan desde el contenedor en:

```
/opt/keycloak/themes
```

---

## 📍 Ubicación en el proyecto

Dentro del repositorio crear estructura:

```
infra/themes/custom-theme/login
```

---

## 📁 Crear archivo de propiedades

Crear:

```
infra/themes/custom-theme/login/theme.properties
```

Contenido:

```properties
parent=keycloak
styles=css/styles.css
```

---

## 📁 Crear carpeta de estilos

Crear:

```
infra/themes/custom-theme/login/resources/css
```

---

## 📁 Crear archivo CSS

Crear:

```
infra/themes/custom-theme/login/resources/css/styles.css
```

Contenido mínimo:

```css
body {
  background-color: #1e293b;
}

.login-pf-page {
  background-color: #1e293b;
}

.card-pf {
  border-radius: 12px;
}
```

---

## 🐳 Montar el theme en el contenedor

Editar:

```
infra/docker-compose.yml
```

Dentro del servicio `keycloak`, añadir volumen:

```yaml
volumes:
  - ./themes/custom-theme:/opt/keycloak/themes/custom-theme
```

---

## ▶️ Reiniciar contenedor

Desde la raíz:

```bash
docker compose down
docker compose up
```

---

## 🧠 Estado actual

* Theme personalizado creado.
* Estructura compatible con Keycloak.
* Montado como volumen en el contenedor.
* En el siguiente paso lo activaremos en el realm.
