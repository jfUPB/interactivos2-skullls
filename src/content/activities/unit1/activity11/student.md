el codigo a realizar lo hice con ayuda de chat gpt, en algunos sectores, poque el codigo me daba problemas con el tamaño de fuente, error que no he podido solucionar


```js
let words = ["cielo", "tierra", "árbol", "agua", "sol", "luz", "noche", "brisa", "camino", "sombras"];
let fonts = ["Georgia", "Verdana", "Courier", "Arial"];
let phrase = "";
let fontSize = 32;
let textX, textY;
let textColor;

function setup() {
  createCanvas(600, 400);
  textAlign(CENTER, CENTER);
  generatePhrase();
}

function draw() {
  background(240);
  fill(textColor);
  textSize(fontSize);
  textFont(random(fonts));
  text(phrase, textX, textY);
}

function mousePressed() {
  generatePhrase();
}

function generatePhrase() {
  phrase = random(words) + " " + random(words) + " " + random(words);
  textX = random(width);
  textY = random(height);
  textColor = color(random(255), random(255), random(255));
}
```
![image](https://github.com/user-attachments/assets/8fca5221-ed64-4b92-902c-45aa86c8a6ab)
