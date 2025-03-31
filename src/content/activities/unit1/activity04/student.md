https://editor.p5js.org/codingtrain/sketches/LXDsoCSZs

El código crea una animación de la curva del dragón, un fractal que se genera duplicando y rotando segmentos de línea. Incluye:

Segmentos dinámicos: Los segmentos se actualizan y crean nuevas generaciones.
Zoom progresivo: Mantiene el fractal centrado mientras crece.
Interpolación suave: Transiciones fluidas entre generaciones.
Modificación 1: Colores dinámicos según la generación
Cambio: En el método show() de la clase Segment, añadimos colores que varían con la generación.

stroke(lerpColor(color('#00f'), color('#f00'), int(log(segments.length) / log(2)) / 10));
Efecto: Los segmentos cambian de azul a rojo, creando un degradado visual dinámico.

Modificación 2: Rotación inicial del fractal
Cambio: En draw(), añadimos rotación progresiva.

rotate(frameCount * 0.002);
Efecto: El fractal gira lentamente, añadiendo una sensación de movimiento continuo.

https://editor.p5js.org/codingtrain/sketches/AoH40T6fV

Descripción del código original
El código simula partículas de arena en una cuadrícula bidimensional.

Partículas caen: Aplican gravedad y pueden desviarse lateralmente.
Interacción: Agregar partículas al arrastrar el mouse, cambiando de color dinámicamente.
Modificación 1: Tamaño dinámico de partículas
Cambio: Las partículas cambian de tamaño según su posición para simular profundidad.

Modificación en draw():

let dynamicSize = w * (1 - j / rows); // Más pequeñas al fondo
square(x, y, dynamicSize);
Efecto: Crea un efecto de perspectiva al hacer que las partículas sean más pequeñas en la parte inferior.

Modificación 2: Arena mágica
Cambio: Agregar partículas que parpadean con colores aleatorios.

Modificación en mouseDragged() y draw():

grid[col][row] = random(1) < 0.1 ? -1 : hueValue; // -1: arena mágica
if (grid[i][j] === -1) fill(random(360), 255, 255); // Parpadeo
Efecto: Algunas partículas destacan con colores brillantes aleatorios.

Resumen
Tamaño dinámico: Efecto de profundidad.
Arena mágica: Partículas parpadeantes para más dinamismo visual.
