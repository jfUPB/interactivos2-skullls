este codigo lo realice con ayuda de chat gpt en ciertas partes especificas, como las barras interactivas y el rango de freguencia

![image](https://github.com/user-attachments/assets/948940ef-f29d-4082-b2d5-b493d88c67a0)


```js
let osc;
let waveType = 'sine'; // Tipo de onda inicial
let freqSlider, ampSlider;

function setup() {
  createCanvas(400, 200);
  
  osc = new p5.Oscillator(waveType);
  osc.freq(440);
  osc.amp(0.5);
  osc.start();
  
  textSize(16);
  
  createP('Frecuencia:');
  freqSlider = createSlider(100, 1000, 440, 1);
  
  createP('Amplitud:');
  ampSlider = createSlider(0, 1, 0.5, 0.01);
  
  let sineButton = createButton('Senoidal');
  sineButton.mousePressed(() => changeWave('sine'));
  
  let squareButton = createButton('Cuadrada');
  squareButton.mousePressed(() => changeWave('square'));
  
  let triangleButton = createButton('Triangular');
  triangleButton.mousePressed(() => changeWave('triangle'));
}

function draw() {
  background(220);
  text('Frecuencia: ' + freqSlider.value() + ' Hz', 20, 50);
  text('Amplitud: ' + ampSlider.value(), 20, 80);
  text('Tipo de onda: ' + waveType, 20, 110);
  
  osc.freq(freqSlider.value());
  osc.amp(ampSlider.value());
}

function changeWave(type) {
  waveType = type;
  osc.setType(type);
}
```
