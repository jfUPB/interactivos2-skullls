La aplicación propuesta es un sistema de música interactiva en tiempo real para múltiples usuarios, utilizando p5.js y la biblioteca p5LiveMedia. La idea es que los usuarios puedan conectarse desde diferentes dispositivos y generar sonidos y ritmos colaborativamente. Cada usuario tendrá la posibilidad de activar distintos instrumentos virtuales, y los datos de su interacción se enviarán en tiempo real a los demás participantes, creando una experiencia musical compartida y dinámica.

## p5LiveMedia se utilizará para:

Transmitir los eventos musicales de cada usuario a los demás clientes conectados en la misma sala.

Sincronizar en tiempo real los sonidos generados para que todos los participantes escuchen la misma composición sin retrasos significativos.

Asignar diferentes instrumentos a cada usuario, permitiendo que cada uno contribuya de manera única a la experiencia musical.

Esta aplicación se puede integrar al proyecto de curso si se está trabajando en experiencias interactivas y colaborativas. En particular, puede ser útil para el museo interactivo basado en experiencias que está en desarrollo para el turismo religioso en Santa Fe de Antioquia. Se podría adaptar para que los visitantes del museo puedan participar en la creación de melodías inspiradas en la música sacra o sonidos ambientales del lugar, mejorando la experiencia inmersiva.

## Tuto izi

-Descarga y configura un servidor local si es necesario 
- Agrega la biblioteca p5LiveMedia en tu proyecto p5.js:

  ```js
  <script src="https://unpkg.com/p5"></script>
  <script src="https://unpkg.com/p5livemedia"></script>
  <script src="https://unpkg.com/tone"></script>
  ```
  Este es el script necesario para agregarla

  Luego creamos un sketch.js y le metemos esto

  ```js
  let p5lm;
  let synth;
  let notes = ["C4", "D4", "E4", "F4", "G4", "A4", "B4", "C5"];

  function setup() {
  createCanvas(800, 600);
  background(200);
  textAlign(CENTER, CENTER);
  textSize(24);
  
  synth = new Tone.Synth().toDestination();
  p5lm = new p5LiveMedia(this, "Data", null, "MusicaColaborativa");
  p5lm.on("data", gotData);
  }

  function draw() {
  background(200);
  text("Presiona teclas del 1 al 8 para tocar notas", width / 2, height / 2);
  }

  function keyPressed() {
  if (key >= '1' && key <= '8') {
    let index = int(key) - 1;
    let note = notes[index];
    synth.triggerAttackRelease(note, "8n");
    p5lm.send(note);
  }
  }

  function gotData(data) {
  synth.triggerAttackRelease(data, "8n");
  }
  ```
Haciendo pruebas con el p5.js aun tengo un problema pero es sencillo de solucionar, y ya carga la pagina 

![image](https://github.com/user-attachments/assets/ebc52449-ba7e-447a-9d3f-146217bad305)

loi siguiente sera hacer pruebas con el servidor
