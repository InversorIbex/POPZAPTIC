# AGENTS.md — Reglas para ChatGPT Codex

Proyecto: POPZAPTIC, videojuego Android arcade 2D en Godot/GDScript.

## Antes de cambiar archivos
1. Leer `docs/ROADMAP.md` y `docs/ART_DIRECTION.md`.
2. Inspeccionar el repositorio y reportar el estado real (prototipo HTML vs Godot).
3. Elegir SOLO el hito solicitado por el usuario. No implementar en bloque todos los hitos.
4. Especificar plan corto de archivos, pruebas y definición de hecho.

## Implementación
- Mantener prototipo HTML inicial en raíz mientras se construye `game/` independiente; no borrarlo ni cambiarlo sin instrucción.
- Para código Godot: elegir versión estable, GDScript, nodos y escenas desacoplados, datos editables, señales, simulación independiente del render.
- Respetar Android portrait, safe areas, input táctil, rendimiento y accesibilidad.
- Arte y efectos originales de calidad comercial: nada de placeholders como entrega final de H1.
- Prohibido hardcodear claves, contraseñas, rutas personales o keystores.
- Si una herramienta/env no está disponible, documentar bloqueo y seguir con pruebas que sí puedan ejecutarse.
- No introducir monetización, anuncios, seguimiento ni conexión obligatoria en la alpha offline.
- No usar servicios de terceros ni assets sin conocer licencia de uso.

## Cierre de cada hito
- Ejecutar validaciones automatizadas y tests manuales cuando el entorno lo permita.
- Comprobar que el juego arranca, que no hay errores de parseo y que las escenas son válidas.
- Reportar: archivos editados, qué funciona, qué no se pudo probar, comandos y resultados, commit.
- No afirmar "validado en Android" sin prueba real en Android.
- No iniciar siguiente hito sin petición/validación del usuario.

## Primer encargo
H0: auditoría, estructura y build Android mínimo. Después H1: un vertical slice visual extraordinario.
