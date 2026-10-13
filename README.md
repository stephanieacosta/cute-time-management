# NubiTime

App web (PWA) de tareas, agenda, hábitos y foco. Sin dependencias ni paso de build: es un `index.html` estático con *service worker*, instalable en móvil y escritorio y con datos guardados en el propio navegador (`localStorage`).

Valores por defecto: piel **Nubi** (cielo), modo **claro**, idioma **español**. Todo se puede cambiar en Ajustes.

## Estructura

| Archivo | Para qué sirve |
| --- | --- |
| `index.html` | La app completa (HTML, CSS y JS en un solo archivo) |
| `manifest.webmanifest` | Manifiesto PWA (nombre, colores, iconos) |
| `sw.js` | Service worker: funciona sin conexión (red primero, caché de respaldo) |
| `vercel.json` | URLs limpias y cabeceras (`sw.js` sin caché, tipo MIME del manifiesto) |
| `favicon.svg` / `favicon.ico` | Icono de pestaña (SVG moderno e ICO de 16/32/48 px) |
| `apple-touch-icon.png` | Icono 180×180 sin transparencia para "Añadir a pantalla de inicio" en iOS |
| `icon-192.png` / `icon-512.png` | Iconos PWA (`any` y `maskable`) |

## Despliegue en Vercel

1. Sube la carpeta a un repositorio, o usa la CLI: `npx vercel` (y `npx vercel --prod`).
2. Framework preset: **Other**. Sin comando de build; directorio de salida: la raíz.

Para probar en local, usa cualquier servidor estático (el service worker no funciona con `file://`):

```bash
npx serve .
```

## Al actualizar la app

Sube el número de versión de la caché en `sw.js` (`const C="nubitime-vN"`) para que los usuarios reciban los cambios. Si añades archivos nuevos, inclúyelos en la lista `A`.

## Datos

Todo se guarda en `localStorage` (clave `nubi-tosti-planner-v1`). La app permite exportar e importar una copia de seguridad desde Ajustes. Limpiar los datos del sitio borra la información.

## Vista previa al compartir el enlace

Igual que Meowney: sin etiquetas `og:*`. WhatsApp toma el `<title>` (al inicio del `<head>`), el `description` corto y el `apple-touch-icon`, con rutas que empiezan en `/`. WhatsApp guarda la vista previa en caché: si ya compartiste el enlace antes, prueba con `?v=2` al final.
