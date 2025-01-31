## Ejemplo 1: Generación de patrones geométricos

Este ejemplo genera patrones geométricos basados en reglas matemáticas. Los parámetros incluyen:

Número de lados: Controla la forma base (triángulo, cuadrado, pentágono, etc.).
Escala: Ajusta el tamaño de los patrones.

Rotación: Define el ángulo de rotación de las formas.

Iteraciones: Determina cuántas veces se repite el patrón.

#Variaciones:
Variación 1: Número de lados = 3, Escala = 50%, Rotación = 45°, Iteraciones = 10.

Variación 2: Número de lados = 6, Escala = 75%, Rotación = 30°, Iteraciones = 5.

#Aplicación potencial:
Este tipo de diseño generativo podría utilizarse en videojuegos para crear texturas procedurales para escenarios, como suelos, paredes o fondos dinámicos.
```js
function setup() {
  createCanvas(400, 400);
  noLoop();
}

function draw() {
  background(255);
  let sides = 6; // Cambiar este valor para variar
  let scale = 0.75; // Cambiar este valor para variar
  let angle = 30; // Cambiar este valor para variar
  let iterations = 5; // Cambiar este valor para variar

  translate(width / 2, height / 2);
  for (let i = 0; i < iterations; i++) {
    rotate(radians(angle));
    drawShape(sides, scale * i * 20);
  }
}

function drawShape(sides, size) {
  beginShape();
  for (let i = 0; i < sides; i++) {
    let angle = TWO_PI / sides * i;
    let x = size * cos(angle);
    let y = size * sin(angle);
    vertex(x, y);
  }
  endShape(CLOSE);
}
```


## Ejemplo 2: Generación de paisajes 3D

Este ejemplo crea paisajes 3D utilizando ruido Perlin. Los parámetros incluyen:

Amplitud: Controla la altura de las montañas.

Detalle: Define el nivel de detalle del terreno.

Color base: Establece el color del paisaje.

# Variaciones:
Variación 1: Amplitud = 100, Detalle = 0.5, Color base = verde.

Variación 2: Amplitud = 200, Detalle = 0.2, Color base = azul.

# Aplicación potencial:
Este tipo de diseño generativo podría aplicarse en juegos de mundo abierto para crear terrenos dinámicos y únicos.

```js
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const geometry = new THREE.PlaneGeometry(10, 10, 100, 100);
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00, wireframe: true });
const plane = new THREE.Mesh(geometry, material);
scene.add(plane);

camera.position.z = 5;

function animate() {
  requestAnimationFrame(animate);
  renderer.render(scene, camera);
}
animate();
```

## Ejemplo 3: Generación de música procedural

Este ejemplo genera música utilizando algoritmos de diseño generativo. Los parámetros incluyen:

Tempo: Controla la velocidad de la música.
Escala musical: Define la tonalidad (mayor, menor, etc.).
Instrumento: Selecciona el tipo de sonido (piano, guitarra, etc.).

#Variaciones:
Variación 1: Tempo = 120, Escala = mayor, Instrumento = piano.

Variación 2: Tempo = 80, Escala = menor, Instrumento = guitarra.

#Aplicación potencial:
Este tipo de diseño generativo podría utilizarse en juegos para crear bandas sonoras dinámicas que se adapten a la acción en tiempo real.

````js
const synth = new Tone.Synth().toDestination();
const scale = ["C4", "D4", "E4", "F4", "G4", "A4", "B4"]; // Escala mayor

Tone.Transport.bpm.value = 120; // Cambiar este valor para variar
Tone.Transport.scheduleRepeat(time => {
  const note = scale[Math.floor(Math.random() * scale.length)];
  synth.triggerAttackRelease(note, "8n", time);
}, "8n");

Tone.Transport.start();
````
