# Classic Physique Tracker

PWA instalable para el plan Upper/Lower de 4 días. Sin build, sin dependencias:
HTML, CSS y JS planos. Los datos viven en `localStorage` del dispositivo.

## Qué hace

- Detecta la sesión del día (Mar · Jue · Sáb · Dom) y calcula series y RIR según la semana del bloque.
- Registra peso × reps por serie, muestra lo que levantaste la vez anterior y arranca el temporizador de descanso al cerrar cada serie.
- Avanza solo al siguiente ejercicio cuando terminas el actual.
- Guarda peso corporal y cintura, con gráficas.
- Exporta e importa un respaldo en JSON.

## Desplegar en GitHub Pages

1. Sube estos archivos a la raíz de un repositorio.
2. Settings → Pages → Source: *Deploy from a branch* → rama `main`, carpeta `/ (root)`.
3. Queda en `https://<usuario>.github.io/<repo>/`.

Todas las rutas son relativas, así que funciona igual en un subdirectorio que en un dominio raíz.
El archivo `.nojekyll` evita que Pages ignore archivos; déjalo.

> Pages gratuito solo publica repos públicos. Si quieres que nadie más lo vea, usa Vercel.

## Desplegar en Vercel

```bash
npm i -g vercel
vercel          # preview
vercel --prod   # producción
```

Proyecto estático, sin framework. `vercel.json` ya fija las cabeceras del service worker.

## Instalar en el teléfono

- **Android / Chrome**: aparece la barra "Instalar" abajo, o menú → *Instalar app*.
- **iPhone / Safari**: Compartir → *Agregar a pantalla de inicio*. iOS no ofrece el botón automático.

Una vez instalada abre sin conexión. Los datos nunca salen del dispositivo.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La app entera: estilos, programa y lógica |
| `sw.js` | Service worker: cachea el shell y las fuentes |
| `manifest.webmanifest` | Nombre, iconos, color y modo standalone |
| `icon-*.png` | Iconos 180 / 192 / 512 y maskable |
| `vercel.json` | Cabeceras para Vercel (Pages lo ignora) |

## Cambiar el programa

Los ejercicios están en la constante `PROGRAM` dentro de `index.html`: cada uno lleva
`s` (series base), `r` (rango de reps), `rir`, `rest` (segundos) y `cue`. Los bloques de
periodización están en `BLOCKS`, justo debajo. No hace falta tocar nada más.
