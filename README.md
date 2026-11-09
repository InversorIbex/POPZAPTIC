# 🎈 POPZAPTIC — Balloon Arcade

Juego arcade **jugable** para móviles y escritorio, sin dependencias ni bibliotecas externas. Explota únicamente los globos del color indicado, evita trampas y encadena combos a lo largo de niveles generados sin fin.

## 🎮 Jugar

Abre `index.html` en un navegador moderno. Para probar la PWA y el modo sin conexión, usa un servidor local:

```bash
python3 -m http.server 8080
```

Después visita `http://localhost:8080` en tu navegador.

## ✨ Mecánicas

- **Niveles infinitos** con objetivos y dificultad creciente.
- **Seis colores**, con un único color válido cada vez y cambios avisados entre fases.
- **Tres vidas**, temporizador, combos hasta x5 y puntuación máxima guardada.
- **Trampas**: bombas y globos peligrosos, además de globos de otros colores.
- **Bonus**: estrellas (+250 puntos), escudos, cámara lenta y vidas extra.
- **Escenarios animados** con cinco paletas que rotan cada cinco niveles.
- **Audio procedural** con Web Audio API y vibración opcional en dispositivos compatibles.
- **PWA instalable** con caché offline; toda la lógica y los gráficos se generan en el navegador.

## 🧱 Tecnología

HTML5, Canvas 2D, JavaScript y CSS. Sin frameworks, sin instalación, sin cuentas, sin anuncios. Diseñado para pantallas verticales Android con `viewport-fit=cover` y escalado para DPI alto.

## 🚀 Publicar con GitHub Pages

Ve a `Settings → Pages` del repositorio y selecciona **Deploy from a branch**, rama `main`, carpeta `/ (root)`. El juego quedará disponible bajo la URL de GitHub Pages del repositorio.

## 📁 Archivos

- `index.html`: menú, motor del juego, estilos, gráficos y sonidos.
- `manifest.webmanifest`: instalación PWA.
- `sw.js`: modo sin conexión.
- `icon.svg`: icono original.

## ⚖️ Licencia

Código y diseños originales del proyecto. Todos los sonidos se sintetizan en el navegador y no requieren archivos de terceros.