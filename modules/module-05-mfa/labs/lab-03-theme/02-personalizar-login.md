# Lab 03 — Theme Personalizado

## Paso 02 — Personalizar la pantalla de Login

---

## 🎯 Objetivo

Modificar la plantilla de login para añadir personalización visual y validar que el theme realmente sobreescribe el original.

---

## 📍 Ubicación

Dentro de:

```
infra/themes/custom-theme/login
```

---

## 📁 Copiar plantilla base

Desde el contenedor puedes inspeccionar la plantilla original o copiarla desde la imagen base.

Crear archivo:

```
infra/themes/custom-theme/login/login.ftl
```

Contenido mínimo personalizado:

```ftl id="q8k2nt"
<#import "template.ftl" as layout>
<@layout.registrationLayout displayMessage=!messagesPerField.existsError('username','password') displayInfo=false; section>

  <#if section = "header">
    <h1 style="color:#38bdf8;">Keycloak Training Portal</h1>

  <#elseif section = "form">
    <div style="padding:20px;">
      ${msg("loginAccountTitle")}
      <@layout.loginForm/>
    </div>

  </#if>

</@layout.registrationLayout>
```

---

## 🧠 Qué estamos haciendo

* Sobrescribimos la plantilla de login.
* Añadimos un encabezado personalizado.
* Mantenemos el formulario original.
* Aplicamos branding básico.

---

## ▶️ Reiniciar contenedor

```bash id="tzlmqg"
docker compose down
docker compose up
```

---

## 📍 Activar theme

En Keycloak:

```
Realm Settings → Themes
```

En campo:

```
Login Theme
```

Seleccionar:

```
custom-theme
```

Guardar.

---

## 🔎 Resultado esperado

Al acceder a login:

* Se muestra el nuevo encabezado.
* Se mantiene el formulario.
* Se aplica el estilo CSS definido.

En el siguiente paso validaremos los cambios y probaremos ajustes adicionales.
