Introducción / Resumen Breve
VisualSync es una aplicación web interactiva que genera visuales dinámicos a partir de un video y música en tiempo real. El sistema permite que un usuario (host) controle la música, mientras otros (guests) cargan videos que se convierten en arte generativo gracias al análisis del audio y las características visuales. El resultado es una experiencia audiovisual colaborativa y personalizada.

Concepto y Narrativa
La idea principal del proyecto es mezclar creatividad, colaboración y tecnología. Queríamos desarrollar una herramienta donde diferentes usuarios pudieran participar en la creación de una pieza visual viva, guiada por la energía del sonido y los elementos del video.

Un usuario actúa como host, eligiendo y reproduciendo música. Los demás pueden subir videos desde sus dispositivos. La app analiza la intensidad, la posición de los píxeles, el brillo y otros datos del video. Al mismo tiempo, interpreta en tiempo real la energía de la música (bajos, medios y agudos) para afectar visualmente un sistema de partículas que reacciona y transforma el video.

VisualSync busca ofrecer una experiencia de creación digital compartida, donde cada ejecución es única porque depende de las decisiones del usuario y del ritmo musical.

Diseño técnico (modelo IPO)
Utilizamos el enfoque IPO (Input – Process – Output) para organizar el diseño del sistema.

Inputs
Intensidad: controlada por el slider intensity-slider en el HTML, se usa para determinar cuántas partículas se generan.

Posición: coordenadas aleatorias dentro del área del video, tomadas para ubicar partículas.

Brillo: ajustado con el slider brightness-slider, que modifica el brillo de las partículas.

Video: cargado por el usuario guest mediante el input de tipo file.

Audio: captado por el host usando p5.FFT, con datos como bajos, medios, agudos y forma de onda.

Proceso
El host reproduce música y la analiza en tiempo real con p5.FFT.
Código clave del host (sketch_host.js):

```js
fft = new p5.FFT();
const bass = fft.getEnergy("bass");
const mid = fft.getEnergy("mid");
const treble = fft.getEnergy("treble");
const waveform = fft.waveform(16);

socket.emit('audio-data', {
  bass: bass / 255,
  mid: mid / 255,
  treble: treble / 255,
  energy: energyLevel,
  waveform: waveform
});
```

Estos datos se envían vía WebSockets al guest:

```js
socket.on('audio-data', (data) => {
  if (userRole === 'guest' && window.myp5) {
    window.myp5.updateAudioData(data);
  }
});
```
El guest recibe los datos, carga el video y extrae píxeles aleatorios para generar partículas visuales.
```js
const x = Math.floor(this.s.random(videoGraphics.width));
const y = Math.floor(this.s.random(videoGraphics.height));
const index = (y * videoGraphics.width + x) * 4;
const r = videoGraphics.pixels[index];
const g = videoGraphics.pixels[index + 1];
const b = videoGraphics.pixels[index + 2];
```
Las partículas reaccionan al ritmo:
```js
if (data.bass > 0.8) {
  for (let i = 0; i < 10; i++) {
    const force = sketch.createVector(Math.cos(angle) * magnitude, Math.sin(angle) * magnitude);
    particle.applyForce(force);
  }
}
```

Outputs
Video visual generativo: una animación dinámica que combina las partículas con el video original del usuario.

Sonido: la música que se sincroniza en todos los clientes desde el host.

Elemento visual (diagrama IPO)
Aquí podés incluir la tabla simple de Inputs / Outputs que hicimos antes, o un esquema visual si lo tenés en imagen.

Tecnologías utilizadas
p5.js: para visualización, dibujo, carga de video y generación de partículas.

p5.sound: para análisis de audio con FFT.

Socket.IO: para la comunicación en tiempo real entre host y guests.

Node.js + Express: para el backend, servidor local.

HTML + CSS: estructura visual e interfaz de la app.

JavaScript: lógica principal del cliente y servidor.

