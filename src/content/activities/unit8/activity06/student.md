Título del proyecto
VisualSync – Arte generativo en colaboración audiovisual

Introducción
VisualSync es una aplicación web colaborativa que genera visuales dinámicos en tiempo real, combinando música y video. El proyecto divide roles entre un host que reproduce música y usuarios invitados (guests) que cargan videos, creando juntos una pieza visual única. La app analiza datos visuales y de sonido para transformarlos en arte generativo.

Concepto y narrativa
Este proyecto busca explorar la creación colectiva en entornos digitales. A partir de un video personal y una pista musical, se genera una pieza visual donde cada partícula reacciona al ritmo, color y energía.

El host define el ritmo con música, y los guests lo interpretan visualmente a través de sus videos. La experiencia generada es única, y representa la combinación de decisiones humanas con procesos algorítmicos en tiempo real.

Diseño técnico – Modelo IPO
Inputs
Intensidad (slider): controla cuántas partículas se generan por cuadro.

Posición: coordenadas aleatorias del video, utilizadas para ubicar partículas.

Brillo (slider): ajusta la luminosidad de las partículas.

Video: archivo cargado por el usuario.

Audio: datos analizados por el host (bajos, medios, agudos, forma de onda, energía).

Proceso
```js
// En el host
const bass = fft.getEnergy("bass");
const mid = fft.getEnergy("mid");
const treble = fft.getEnergy("treble");
socket.emit('audio-data', { bass, mid, treble, ... });
```
```js
// En el guest
const r = videoGraphics.pixels[index];
const g = videoGraphics.pixels[index + 1];
const b = videoGraphics.pixels[index + 2];
const particle = new Particle(x, y, [r, g, b], sketch, intensity);
```

El host analiza la música y transmite los datos por WebSocket.

El guest usa los datos para crear visuales a partir de píxeles del video, generando partículas que se comportan según el audio.

Outputs
Visual generativo: animación de partículas sincronizada con el video y música.

Sonido: reproducción del audio para todos los usuarios conectados.

Video demostrativo


Tecnologías utilizadas
p5.js – visuales y manipulación de video/audio

p5.sound – análisis de audio en tiempo real

Node.js + Express – servidor web local

Socket.IO – comunicación en tiempo real entre clientes

HTML + CSS – interfaz de usuario

JavaScript – lógica del prototipo

Tutorial paso a paso
Requisitos
Node.js instalado

Editor de código (recomendado: VSCode)

Pasos

Cloná el repositorio o descargá el proyecto.

En la carpeta raíz, ejecutá en consola:
npm install
npm run dev

Abrí tu navegador en http://localhost:3000

La primera pestaña será el host (controla la música).

Abrí una segunda pestaña o navegador: este será el guest (carga el video).

En el guest, hacé clic en “Seleccionar video” y luego “Reproducir video”.

Ajustá los sliders de intensidad, brillo y color para ver cómo cambia la animación.

Observá cómo la música afecta el comportamiento de las partículas.
