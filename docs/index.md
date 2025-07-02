---
title: Home
layout: home
nav_order: 1
description: "Blog técnico colaborativo para compartir conocimiento, experiencias y novedades del equipo."
permalink: /
---

# Bienvenido al Blog Técnico de la Software Factory
{: .fs-9 }

Un espacio colaborativo para compartir conocimiento, experiencias y novedades del mundo del desarrollo de software.
{: .fs-6 .fw-300 }

[Publicar un artículo](/como-publicar/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Ver todos los artículos](/posts/){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## Artículos destacados

<div class="featured-posts" style="display: flex; flex-wrap: wrap; gap: 2rem;">
  {% assign destacados = site.posts | sort: "date" | reverse | slice: 0, 3 %}
  {% for post in destacados %}
    <div class="post-card" style="flex: 1 1 300px; border: 1px solid #eee; border-radius: 8px; padding: 1rem;">
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
      <div style="font-size: 0.9em; color: #888;">
        {{ post.date | date: "%d/%m/%Y" }} &mdash; {{ post.author | default: "Autor desconocido" }}
      </div>
      <div class="post-excerpt" style="margin-top: 0.5em;">
        {{ post.excerpt | markdownify | truncatewords: 30 }}
      </div>
      <a href="{{ post.url | relative_url }}" class="btn btn-outline-primary btn-sm" style="margin-top: 0.5em;">Leer más</a>
    </div>
  {% endfor %}
</div>

---

## ¿Qué encontrarás aquí?

- Tutoriales y guías técnicas
- Experiencias de proyectos reales
- Buenas prácticas de desarrollo
- Novedades y tendencias tecnológicas
- Opiniones y debates sobre herramientas y metodologías

---

## Sobre el proyecto

Este blog es una iniciativa interna de la software factory para fomentar el intercambio de conocimiento y la mejora continua.  
Todos los miembros del equipo están invitados a contribuir con artículos, comentarios y sugerencias. ¡Tu aporte es valioso para el crecimiento de todos!

---

## Licencia

El contenido publicado es propiedad de sus autores y se distribuye bajo la licencia MIT, salvo que se indique lo contrario.

---

¿Quieres publicar tu propio artículo?  
Consulta la [guía para publicar](/como-publicar/) o contacta a los administradores del blog.

