# POPZAPTIC — ART DIRECTION / BIBLIA VISUAL

## Sensación visual
"Sweet, glossy, joyful arcade": estética 2D casual premium original. Referencias conceptuales mostradas en el chat son un objetivo de calidad, no recursos con derechos de reutilización. Crear diseño propio de globos, personajes, escenarios, botones y FX; no copiar marcas ni ilustraciones protegidas.

## Idioma visual
- Arte 2D vectorial/raster de alta calidad, bordes suaves, formas redondeadas y amigables.
- Globos ligeramente volumétricos, gradientes radiales, dos reflejos de luz, ribete tenue, sombra y nudo visible; añadir cuerda discreta.
- Pequeña personalidad (caras opcionales en ciertas skins) sin complicar la identificación del color.
- Burbujas, nubes acolchadas, estrellas y elementos flotantes; evita saturación de partículas delante de globos táctiles.
- HUD con tipografía redondeada legible, jerarquía fuerte. No usar emojis como arte final. Botones grandes con estados pressed/disabled.
- Animaciones squash & stretch: entrada 180–260ms, pop 100–180ms, chispa 250–450ms, victoria 1–2 s; adaptación a reduce-motion.
- Un fondo atractivo nunca debe reducir contraste entre globos válidos y erróneos. Añadir halo/silueta según la necesidad.

## Colores de globos iniciales
- Rosa rojizo #FF5B86 — icono de corazón
- Azul cielo #49B8FF — icono de gota
- Amarillo #FFD44D — icono de estrella
- Verde menta #4DDF9E — icono de hoja
- Violeta #AE79FF — icono de luna
- Naranja #FF9A55 — icono de sol
Estos hex son BASES; render final usa gradientes, sombras y highlights. Cada objetivo aparece como color + nombre + icono.

## Cinco mundos originales
1. Candy Sky: lavanda/rosa, nubes mousse, destellos.
2. Tropical Sunset: melocotón/coral, hojas, horizonte cálido.
3. Kawaii Cosmos: azul profundo/morado, planetas adorables, cometas lentos.
4. Dream Ocean: turquesa/azul, burbujas translúcidas, coral suave.
5. Neon Party: azul noche/magenta, luces volumétricas contenidas, confeti.

Cada mundo: fondo lejano + medio + frontal, parallax suave, overlays atmosféricos, paleta de UI adaptada; cambio de mundo cada 5 niveles (repetición cíclica con variantes para el infinito).

## Pantallas
1. Splash con identidad POPZAPTIC
2. Menú principal: logo, globo hero, JUGAR, botón desafío diario (cuando exista), sonido/ajustes
3. HUD de partida: nivel, progreso, vidas, combo, puntos, PAUSA y color objetivo GRANDE
4. Cambio de objetivo: aviso 0.6–1s; no se aceptan taps durante transición
5. Fin de nivel: estrellas, mejor combo, puntuación y siguiente nivel
6. Game over: puntuación, récord, repetir
7. Futuras: Duelo (VS con barras individuales y marcador), lobby Party (avatars + código + preparado), podio.

## Guardarraíles del diseño
- Área principal jugable sin scroll y lejos de notch/safe-area; 9:16 adaptable a pantallas altas/cortas.
- Targets accesibles al dedo y con hitboxes más generosas que la ilustración.
- Indicaciones por color, palabra e icono; no exigir audio ni vibración.
- No mostrar publicidad, ventanas emergentes ni efectos desorientadores durante el momento de toque.
- Reservar presupuesto para 60 FPS; efectos degradables por calidad gráfica.

## Pipeline de arte
Antes de generar producción masiva: diseñar una hoja maestra de globos, 1 escenario y 1 pantalla HUD; revisar en Android. Posteriormente generar assets consistentes: transparencias reales, versiones alta/normal resolución, naming, atlas, licencia/origen documentado; evitar recursos enlazados desde URLs temporales.

## Definition of Done visual
Captura de móvil real a pantalla completa, HUD claramente legible, brillo y volumen reconocibles, partículas fluidas, escena sin placeholders. El usuario debe aprobar el *vertical slice* H1 antes de desarrollar todos los niveles.
