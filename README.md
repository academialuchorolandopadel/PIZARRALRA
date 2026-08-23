# Pizarra Táctica · Academia LR

App de pizarra táctica de pádel: cancha con vidrios y rejas numerados a escala real,
fichas y siluetas de jugadores + pelota que arrastrás desde un banco, pasos animados,
biblioteca de jugadas guardadas en el dispositivo, y exportación como imagen.

## Publicar en GitHub Pages (gratis, en 3 pasos)

1. Creá un repositorio nuevo en GitHub (puede ser público o privado) y subí **todos los
   archivos de esta carpeta** manteniendo la estructura tal cual está:

   ```
   index.html
   manifest.json
   sw.js
   icons/
     icon-32.png
     icon-180.png
     icon-192.png
     icon-512.png
   ```

2. En el repositorio: **Settings → Pages → Build and deployment → Source: "Deploy from a
   branch"** → elegí la rama `main` y la carpeta `/ (root)` → **Save**.

3. Esperá 1-2 minutos. GitHub te va a dar una URL del estilo:
   `https://tu-usuario.github.io/tu-repo/`

   Esa es la URL que abrís en el celular e instalás como app (ver abajo).

No hace falta configurar nada más: no hay build, no hay dependencias que instalar, es
HTML/CSS/JS puro.

## Instalar como app en el celular

1. Abrí la URL de GitHub Pages en el navegador del celular (Chrome en Android, Safari en
   iPhone).
2. **Android (Chrome)**: menú (⋮) → "Agregar a pantalla de inicio" / "Instalar app".
3. **iPhone (Safari)**: botón Compartir → "Agregar a inicio".
4. Te queda un ícono propio (el logo LR) que abre a pantalla completa, sin la barra del
   navegador.

## Modo sin conexión

A diferencia de la versión que corría dentro de Claude, esta versión tiene un service
worker real (`sw.js`) que cachea la app la primera vez que la abrís con internet. Después
de esa primera visita, funciona sin conexión: cancha, fichas, pasos, dibujo, guardado de
jugadas — todo sigue andando offline, porque además el guardado ahora usa el
almacenamiento propio del navegador (`localStorage`) en vez de depender de un servidor.

**Importante:** `localStorage` guarda los datos en el navegador de **ese** celular o
tablet. Si abrís la app en otro dispositivo, no vas a ver las mismas jugadas guardadas —
cada dispositivo tiene su propia biblioteca. Si en algún momento necesitás que la
biblioteca se sincronice entre varios dispositivos, avisame: eso ya requeriría un backend
real (una base de datos en la nube), que es un paso más grande.

## Actualizar la app

Cuando quieras cambiar algo, editá `index.html` (o los otros archivos) y subí los cambios
al repo. GitHub Pages actualiza la URL sola en 1-2 minutos. El service worker revisa si
hay una versión nueva cada vez que hay conexión, así que los usuarios la reciben la
próxima vez que abren la app con internet.

## Estructura de archivos

- **`index.html`** — la app completa (HTML + CSS + JS en un solo archivo).
- **`manifest.json`** — metadata de instalación (nombre, ícono, colores).
- **`sw.js`** — service worker para el modo offline.
- **`icons/`** — el ícono de la app en distintos tamaños, generado desde el logo real de
  la Academia LR.
