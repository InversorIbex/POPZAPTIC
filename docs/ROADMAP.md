# POPZAPTIC — ROADMAP DE PRODUCCIÓN ANDROID
Versión 1.0 del plan · 2026-11-09 · Responsable de implementación: ChatGPT Codex

## Visión
Juego arcade 2D Android vertical (*portrait*) premium y original. Regla de oro: SOLO hay un color objetivo activo en cada instante; tocar globos de otros colores da penalización. Partidas cortas, feedback excepcional, accesible, divertido, escalable a multijugador.

**Prioridad:** experiencia táctil, fluidez y calidad visual antes que cantidad de modos o servicios online.

## Estado de partida y política de migración
El repositorio ya contiene un prototipo funcional HTML5 en `index.html`, `sw.js`, `manifest.webmanifest`, `icon.svg`.
- No borrar ni sobrescribir el prototipo web sin autorización.
- Crear proyecto Android de Godot en `game/`. El prototipo es referencia de reglas, NO se copia HTML a una WebView.
- Usar versión estable Godot 4.x instalada y fijar versión exacta en documentación; preferir GDScript para facilidad de Android.
- No conectar backend, SDK publicitario ni pagos hasta superar las puertas de calidad offline.

## Dirección del producto
**Modos planeados**
1. **INFINITO:** principal, jugable offline, niveles procedimentales y mejores puntuaciones.
2. **DESAFÍO DIARIO:** misma semilla para todos; inicialmente offline/local, clasificación global solo con verificación servidor.
3. **DUELO 1 vs 1:** 60 segundos, mismo recorrido determinista, puntuación verificada; matchmaking y partidas con amigos.
4. **POP PARTY:** salas de 4–8 jugadores, 3 rondas de 45 segundos, público/privado con código, clasificación y podio.

**Economía:** sin pay-to-win. Cosméticos, logros y progresión optativa después del núcleo. No introducir compras ni anuncios en la primera alpha.

## Diseño del gameplay
- Seis colores seleccionables, cada uno representado también por nombre/icono para accesibilidad.
- Objetivo de aciertos por nivel, temporizador razonable, 3 vidas, combo creciente con máximo establecido por configuración.
- Cambios de objetivo siempre anticipados (aviso y bloqueo/transición breve), nunca una penalización sorpresiva.
- Trampas: bomba (marcada), señuelo, globo camaleón (telegráfico), globo congelado, variación de tamaños, vientos.
- Power-ups: puntos, escudo, vida extra con límite, cámara lenta y modo FIEBRE por racha.
- Garantizar aparición de suficientes globos válidos, área de toque generosa y metas alcanzables; evitar superposiciones injustas.
- Generación determinista por semilla para repetir y comparar partidas, independiente del frame rate.
- Asegurar que tocar fuera del globo no penaliza; no bloquear jugabilidad por falta de sonido, permisos o conexión.

## Principios de ingeniería
- Cada hito: implementar -> validar sintaxis/escenas/pruebas -> ejecutar -> screenshot o vídeo de evidencia cuando se pueda -> commit -> breve informe con archivos, riesgos y siguiente tarea.
- Mantener lógica de simulación y puntuación independiente de dibujos/partículas/HUD. El estado del juego es determinista.
- Datos de balance en recursos/configuración, nunca reglas dispersas en scripts.
- Definir eventos tipados: balloon_spawned, balloon_popped, wrong_pop, target_changed, level_complete, run_ended.
- Estructura orientativa:
  - `game/project.godot`
  - `game/scenes/menu/`, `game/scenes/game/`, `game/scenes/ui/`
  - `game/scripts/core/`, `game/scripts/systems/`, `game/scripts/ui/`
  - `game/assets/art/`, `game/assets/audio/`, `game/assets/fonts/`
  - `game/data/`, `game/tests/`
- Commits pequeños, mensajes descriptivos. No secretos, contraseñas, keystores ni credenciales en Git.

## Hitos y criterios de aceptación

### H0 — AUDITORÍA Y BOOTSTRAP (P0)
1. Inspeccionar repositorio y documentar mecánicas del prototipo actual.
2. Confirmar versión estable de Godot, entornos Windows/WSL/Android y configuración Android SDK.
3. Crear `game/` y proyecto Godot vacío, portrait, escalado a pantallas diversas, y pantalla de prueba.
4. Añadir `.gitignore` apropiado y guía reproducible de ejecución.

**Hecho si:** se abre en Godot sin errores y genera un build Android debug instalable, o se documenta con claridad la dependencia externa que impide el export; el prototipo web no se altera.

### H1 — VERTICAL SLICE VISUAL (P0; NO construir todavía todo el juego)
1. Una escena jugable de un único nivel con *arte final orientativo*, no placeholders geométricos.
2. Fondos multicapa animados, un cielo pastel, nubes, destellos y profundidad (parallax).
3. Globos originales satinados con reflejos, sombra, brillo, deformación al explotar, al menos 4 colores.
4. Partículas, confeti, pop elástico, sonido agradable, vibración opcional.
5. HUD legible, pausas, transiciones, efectos de acierto/error y accesibilidad.

**Hecho si:** en un Android físico, golpear 20 globos seguidos se siente preciso y satisfactorio; aspecto equiparable al moodboard, legibilidad alta y sin tirones apreciables. Capturas de evidencia.

### H2 — CORE LOOP COMPLETO (P0)
1. Máquina de estados: MENU -> LEVEL_INTRO -> PLAYING -> TARGET_WARNING -> PAUSED -> LEVEL_CLEAR / GAME_OVER.
2. Spawn de globos según semilla; trayectorias y hitboxes estables; 1 color objetivo a la vez.
3. Cambio de objetivo telegráfico, 3 vidas, combo, puntos, temporizador y objetivo completado.
4. Niveles N+1 generados sin fin, con límites explícitos para que la dificultad no crezca sin control.
5. Continuar, reintentar, salir a menú, guardar récord y nivel más alto.
6. Pruebas de lógica sin depender del render; duplicación accidental de taps prohibida.

**Hecho si:** 20 niveles consecutivos sin bloqueos, simulación sin depender de FPS, progreso guardado tras cerrar app; ningún nivel imposible en batería de semillas automatizadas.

### H3 — MECÁNICAS ESPECIALES Y BALANCE (P1)
1. Bombas, camaleones, señuelos, bonus, escudo, ralentización, corazones y FIEBRE.
2. Al menos 5 modificadores de nivel: lluvia, zigzag, viento, gigante, microglobos.
3. Dificultad justa; poder llegar lejos por habilidad, sin cambios de color sorpresa.
4. Señalización además del color; ajustes sonido/vibración/reducción movimiento.
5. Estadísticas locales de partidas (sin datos personales).

**Hecho si:** cada bonus tiene efecto real y prueba; trampas diferenciables y 1000 niveles simulados sin estados sin salida.

### H4 — PRESENTACIÓN PREMIUM Y MUNDOS (P1)
1. Cinco biomas originales: Candy Sky, Tropical Sunset, Kawaii Cosmos, Dream Ocean y Neon Party.
2. Fondo de varias capas con movimiento sutil, paletas día/noche y transiciones cada cinco niveles.
3. Menú, selección de modo, resultados, recompensas, animaciones y audio sin sobresaturación.
4. Optimización de atlas/texturas, pooling para globos/partículas, presupuesto GPU/CPU.
5. Icono, splash y capturas iniciales originales.

**Hecho si:** 60 FPS objetivo en gama media compatible y alta, sin pérdidas notables al activar efectos, y consumo/temperatura razonables en sesiones de 15 minutos. Incluir un modo de efectos reducidos si es necesario.

### H5 — RETENCIÓN OFFLINE / DESAFÍO DIARIO (P1)
1. Misión diaria, 3 objetivos rotativos, racha de días opcional, logros locales.
2. Desafío diario con semilla estable por día UTC (documentar zona horaria), una entrada puntuable por usuario/dispositivo local.
3. Progresión cosmética sin ventajas competitivas; recompensas no monetizadas.
4. Menú de ajustes y datos locales; recuperación de guardado, pruebas de corrupción y reinicios.

**Hecho si:** el juego es completo y divertido sin cuenta ni conexión y se prueba en teléfono.

### H6 — BETA ANDROID Y CALIDAD (P0 para lanzamiento)
1. Exportar APK debug + AAB release con firma segura fuera de Git.
2. Pruebas automatizadas + test manual Android real (incluyendo Samsung S25 Ultra y un gama media).
3. Compruebar rotación (forzar portrait), interrupciones, pausas, reanudar, llamadas, pérdida de audio, distintos DPI.
4. Medir FPS/tiempo de frame, consumo, crash y tamaños instalables; usar umbrales definidos por hardware.
5. Cumplir requisitos actuales Google Play: nivel API vigente, ficha, privacidad, clasificación por edades, declaración de datos.

**Hecho si:** prueba cerrada estable con cero fallos bloqueantes y controles precisos.

### H7 — MULTIJUGADOR 1 VS 1 (P2; tras beta offline)
1. Definir backend (Firebase / servicio propio) y costes operativos antes de implementarlo.
2. Auth invitado y opcional cuenta; sesiones de juego con semilla y versión de reglas fijadas por servidor.
3. Dos clientes juegan secuencias equivalentes durante 60s; servidor recibe entradas o pruebas de partida, comprueba plausibilidad, calcula resultado y determina ganador.
4. Amigo con código, matchmaking, reconexión, abandono y revancha; sincronizar temporizador.
5. Rating tras suficiente población; nunca resultados basados solo en un número enviado por cliente.
6. Gestión de privacidad, cuentas, eliminación de datos y seguridad antiabuso.

**Hecho si:** tests con dos Android distintos y emulación de latencia, desconexión y fraude básico; ganador correcto y estados consistentes.

### H8 — POP PARTY 4–8 (P3)
1. Salas privadas con código, lobby, anfitrión y preparación; salas públicas si hay usuarios suficientes.
2. Tres rondas de 45s, mismos parámetros de reto por ronda, marcador entre rondas, podio final.
3. Reconexión, límite por sala, gestión de abandonos y prevención de spam.
4. Métricas mínimas para dimensionar costes por concurrencia.

**Hecho si:** 8 clientes simulados + pruebas reales no corrompen el estado de sala y cierran con ranking determinista.

### H9 — PUBLICACIÓN Y EVOLUCIÓN (P2)
1. Release testing Google Play; pruebas de ANR/crashes, privacidad, requisitos vigentes y capturas reales.
2. Telemetría respetuosa de privacidad y con consentimiento cuando corresponda.
3. Ajustar retención D1/D7 y duración de sesión sin perjudicar el diseño.
4. Solo después valorar monetización cosmética/ads no intrusivos, con revisión de políticas.

## Backlog: dejar fuera de los primeros hitos
Chat público, perfiles sociales complejos, avatares 3D, marketplace, pase de batalla de pago, infraestructura de torneos masivos, pay-to-win, seguimiento continuo de ubicación, personalización de anuncios.

## Regla de desbloqueo
No empezar H7/H8 si H1–H6 no tienen un buen núcleo Android. Si H1 no alcanza la dirección artística, NO acelerar a H2: cerrar primero la calidad visual y táctil.

## Entregables de cada hito
- Código funcional y escena inicial ejecutable.
- Pruebas realizadas con resultado y comando exacto.
- APK debug cuando el cambio afecte Android y el entorno lo permita.
- Screenshot/video de UI y resultado de profiling cuando aplique.
- Commit + nota corta de cambios, pendientes y pasos para reproducir.

## Instrucción operativa para Codex
Trabajar un hito cada vez. Leer `AGENTS.md`, `docs/ROADMAP.md`, `docs/ART_DIRECTION.md`; implementar solo el alcance del hito actual. Nunca reportar pruebas no realizadas. No pasar al siguiente hito sin revisión del usuario.
