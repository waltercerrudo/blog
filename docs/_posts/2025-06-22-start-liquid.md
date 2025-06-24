---
title: Fundamentos de Liquid y su Uso en Jekyll
description: Fundamentos
author: wcerrudo
layout: default
grand_parent: Layout
date: 2025-06-22 11:33:00 +0800
categories: [jekyll, liquid]
tags: [typography]
pin: true
math: true
mermaid: true
image:
  path: /img/liquid.png
  alt: Liquid.
---

**Liquid** es un lenguaje de plantillas desarrollado por Shopify. Es el motor de plantillas que usa Jekyll para generar contenido dinámico en sitios estáticos.

## 📌 ¿Qué es Liquid?

Liquid permite incluir lógica básica en archivos HTML o Markdown para mostrar contenido dinámico basado en variables, bucles, condiciones, y más.

---

## 🔧 Sintaxis Básica

### 1. **Variables**


```liquid
{% raw %}
{{site.title}}
{{page.title}}
{% endraw %}
```


Se usan dobles llaves {% raw %}`{{ }}`{% endraw %} para imprimir valores.

### 2. **Filtros**


```liquid
{% raw %}
{{ "hola mundo" | upcase }}   => HOLA MUNDO
{{ post.date | date: "%Y" }} => 2025
{% endraw %}
```


### 3. **Etiquetas**


```liquid
{% raw %}
{% if page.title == "Inicio" %}
  <p>Estás en la página principal</p>
{% endif %}
{% endraw %}
```


---

## 🔁 Estructuras de Control

### **Condicionales**


```liquid
{% raw %}
{% if user %}
  Hola, {{ user.name }}!
{% else %}
  Bienvenido, visitante.
{% endif %}
{% endraw %}
```


### **Bucles**


```liquid
{% raw %}
{% for post in site.posts %}
  <h2>{{ post.title }}</h2>
  <p>{{ post.date | date: "%d-%m-%Y" }}</p>
{% endfor %}
{% endraw %}
```


---

## 📁 Variables Comunes en Jekyll

- `site`: Contiene datos del sitio entero (configuración, páginas, posts, etc.)
- `page`: Representa la página actual
- `post`: Accede a atributos de cada post individual
- `paginator`: Si tienes paginación habilitada

---

## 🧰 Includes y Layouts

### Includes


```liquid
{% raw %}
{% include header.html %}
{% endraw %}
```

```liquid
{% raw %}
{% include card.html title="Producto" %}
{% endraw %}
```


### Layouts

Definen la estructura base para una página:


```html
{% raw %}
<!-- _layouts/default.html -->
<html>
  <body>
    {{ content }}
  </body>
</html>
{% endraw %}
```


En una página Markdown:


```markdown
{% raw %}
---
layout: default
title: Sobre mí
---
{% endraw %}
```


---

## 📝 Archivos de Datos

Puedes usar archivos YAML/JSON/CSV dentro de la carpeta `_data/`:


```liquid
{% raw %}
{% for miembro in site.data.equipo %}
  <li>{{ miembro.nombre }} - {{ miembro.rol }}</li>
{% endfor %}
{% endraw %}
```


---

## 🔐 Buenas Prácticas


```liquid
{% raw %}
{{ page.author | default: "Anónimo" }}
{% endraw %}
```


- Escapa caracteres para evitar errores con `escape` o `escape_once`.
- Divide lógica compleja en includes reutilizables.

---

## 📚 Recursos Adicionales

- [Documentación de Liquid (Shopify)](https://shopify.github.io/liquid/)
- [Guía oficial de Jekyll](https://jekyllrb.com/docs/liquid/)
