# Guía: Crear un blog con Hugo en Ubuntu

**Blog:** Prácticas de electricidad con TinkerCad  
**Tema:** Paper  
**Sistema operativo:** Ubuntu

---

## Fase 1 — Instalación

### Paso 1: Instalar Hugo

La forma más sencilla y actualizada es usar el gestor de paquetes `snap`:

```bash
sudo snap install hugo
```

> **Nota:** También puedes usar `sudo apt install hugo`, pero la versión del repositorio APT suele ser antigua. Con snap obtienes la versión más reciente.

### Paso 2: Verificar la instalación

```bash
hugo version
```

Deberías ver algo como: `hugo v0.xx.x ...`

### Paso 3: Instalar Git (si no lo tienes)

Git es necesario para gestionar los temas de Hugo:

```bash
sudo apt install git
```

---

## Fase 2 — Crear el sitio

### Paso 4: Crear el nuevo sitio Hugo

Elige la carpeta donde quieras guardar el proyecto (por ejemplo, tu carpeta personal) y ejecuta:

```bash
cd ~
hugo new site practicas-electricidad
cd practicas-electricidad
```

Esto crea la estructura de carpetas del blog.

### Paso 5: Inicializar repositorio Git

Dentro de la carpeta del sitio, inicia un repositorio Git:

```bash
git init
```

### Paso 6: Instalar el tema "Paper"

Añade el tema como submódulo Git (método recomendado):

```bash
git submodule add https://github.com/nanxiaobei/hugo-paper themes/paper
```

Esto descarga el tema en la carpeta `themes/paper`.

---

## Fase 3 — Configurar el blog

### Paso 7: Editar el archivo de configuración

Abre el archivo `hugo.toml` (o `config.toml`) con un editor de texto:

```bash
gedit hugo.toml
```

Reemplaza su contenido con lo siguiente:

```toml
baseURL = "http://localhost/"
languageCode = "es-ES"
title = "Prácticas de electricidad con TinkerCad"
theme = "paper"

[params]
  color = "linen"
  twitter = ""
  github = ""
  description = "Blog de prácticas de electricidad con TinkerCad"
```

> **Nota:** Puedes cambiar el valor de `color` por: `linen`, `wheat`, `beige`, `moccasin`...

---

## Fase 4 — Crear contenido

### Paso 8: Crear tu primera entrada

Genera un nuevo artículo (post) desde la terminal:

```bash
hugo new posts/primera-practica.md
```

Se crea el archivo en `content/posts/`. Ábrelo para editarlo:

```bash
gedit content/posts/primera-practica.md
```

Verás una cabecera como esta. Cambia `draft: true` a `false` para publicarlo:

```markdown
---
title: "Primera práctica"
date: 2024-01-01
draft: false
---

Escribe aquí el contenido de tu práctica en formato Markdown.
```

> **Consejo:** El formato Markdown es muy sencillo. Algunos ejemplos:
> - `## Título` → crea un subtítulo
> - `**texto**` → texto en **negrita**
> - `![descripción](ruta-imagen.jpg)` → inserta una imagen

---

## Fase 5 — Previsualizar y publicar

### Paso 9: Lanzar el servidor local

Previsualiza el blog en tu navegador antes de publicarlo:

```bash
hugo server -D
```

Abre tu navegador y ve a:

```
http://localhost:1313
```

> El flag `-D` muestra también los borradores. Pulsa `Ctrl+C` en la terminal para parar el servidor.

### Paso 10: Generar el sitio estático

Cuando quieras publicar, genera los archivos HTML finales:

```bash
hugo
```

Los archivos listos para subir al servidor se guardan en la carpeta `public/`.

---

## Resumen de comandos

| Paso | Comando |
|------|---------|
| Instalar Hugo | `sudo snap install hugo` |
| Instalar Git | `sudo apt install git` |
| Crear sitio | `hugo new site practicas-electricidad` |
| Añadir tema | `git submodule add https://github.com/nanxiaobei/hugo-paper themes/paper` |
| Nueva entrada | `hugo new posts/nombre-practica.md` |
| Previsualizar | `hugo server -D` |
| Generar sitio | `hugo` |

---

## Estructura de carpetas del proyecto

```
practicas-electricidad/
├── archetypes/
├── content/
│   └── posts/           ← Aquí van tus entradas
├── themes/
│   └── paper/           ← El tema instalado
├── static/              ← Imágenes y archivos estáticos
├── layouts/
└── hugo.toml            ← Archivo de configuración
```

---

*Guía preparada para el IES de Andalucía — Departamento de Tecnología*
