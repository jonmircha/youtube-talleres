# Taller _PWA_: convierte tu sitio web en aplicación 📱

Los códigos de mi taller de _Progressive Web Apps_ en _YouTube_. Convertimos una _landing page_ sencilla, la de **#ProgramadorFitness**, en una aplicación web progresiva que se instala en el celular y en el escritorio, abre en su propia ventana y funciona sin conexión.

## Los videos

| #   | Video                                                                                          | Archivos                              |
| --- | ---------------------------------------------------------------------------------------------- | ------------------------------------- |
| 1   | [¿Qué es una _PWA_? Instálala en tu celular y tu escritorio](https://youtu.be/9oQIylJ-JpU)     |                                       |
| 2   | [La página base: _HTML_, _CSS_ y un servidor local](https://youtu.be/UUL4mdq5rf0)              | `index.html`, `style.css`             |
| 3   | [`manifest.json` y metaetiquetas: nombre, colores e iconos](https://youtu.be/0cSG5kM7bZ8)      | `index.html`, `manifest.json`, `img/` |
| 4   | [Registra el _service worker_ y define qué guardar en caché](https://youtu.be/RBckJ0GbC7g)     | `script.js`, `sw.js`                  |
| 5   | [`install`, `activate` y `fetch`: la caché del _service worker_](https://youtu.be/uLVxHxDjuyU) | `sw.js`                               |
| 6   | [Instala tu _PWA_ y publícala con _HTTPS_ en _GitHub Pages_](https://youtu.be/OitHrYSjCyE)     |                                       |

Todo el taller, en orden, está en su [lista de reproducción](https://www.youtube.com/playlist?list=PLvq-jIkSeTUYIw8CP2AP7QJs4GeeZdvs6).

## Cómo probarlo

Un _service worker_ solo se registra en un sitio con _HTTPS_ o en `localhost`, así que abrir el `index.html` con doble clic no basta: sírvelo desde un servidor local. En el taller uso _Apache_; cualquier otro funciona igual, por ejemplo:

```bash
cd pwas
python3 -m http.server 8080
```

Abre `http://localhost:8080` y, en las herramientas de desarrollo de _Chrome_, entra a la pestaña **Application**: ahí ves el _manifest_, el _service worker_ y la caché.

> Si cambias un archivo, sube la versión de `CACHE_NAME` en `sw.js` (`v1` → `v2`). El _service worker_ responde desde la caché, así que sin ese cambio seguirás viendo la versión anterior.

## Funcionando

Así se ve publicado en _GitHub Pages_: https://jonmircha.github.io/youtube-talleres/pwas/

En el video lo publico desde la rama `gh-pages`. Hoy _GitHub Pages_ también publica desde `main`, y así se publica este repositorio.

## Cambios respecto al video

El código es el del taller, con tres ajustes para que siga funcionando:

- **_Font Awesome_ se carga desde _jsDelivr_** (versión 5.15.4) y no desde `use.fontawesome.com`. Ese _CDN_ no permite que otro sitio lea sus archivos (_CORS_), así que `cache.addAll()` fallaba y la caché quedaba vacía: sin conexión, la página no cargaba.
- **La fuente de _Raleway_** que guarda el _service worker_ es la que _Google Fonts_ sirve hoy. Su URL cambia con cada versión de la fuente; si la tipografía no aparece sin conexión, revisa que coincida con la de su hoja de estilos.
- **Las rutas de `apple-touch-icon` y `apple-touch-startup-image`** apuntan a `img/`, donde está la imagen.

## Mis redes

- 🦊 Visita mi web https://jonmircha.com
- 🔔 Suscríbete al canal https://youtube.com/@jonmircha
- 📬 Suscríbete a mi newsletter https://jonmircha.com/newsletter
- 🌮 ¿Me invitas un taco? https://jonmircha.com/taco
