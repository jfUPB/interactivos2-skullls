El enerative desing que escogi fue el siguiente, que es un circulo cromaico que cambia dependiende de la posicion del crsor 

![image](https://github.com/user-attachments/assets/231d2cc6-b157-4b4d-9a21-8fc58c512279)


este es el codigo al que pude llegar 

```js
let segmentos = 360;
let radio = 300;

function setup() {
  createCanvas(800, 800);
  noStroke();
  colorMode(HSB, 360, 100, 100);
}

function draw() {
  background(360, 0, 100);
  let pasoAngulo = 360 / segmentos;

  beginShape(TRIANGLE_FAN);
  vertex(width / 2, height / 2);

  for (let angulo = 0; angulo <= 360; angulo += pasoAngulo) {
    let vx = width / 2 + cos(radians(angulo)) * radio;
    let vy = height / 2 + sin(radians(angulo)) * radio;
    fill(angulo, 100, 100);
    vertex(vx, vy);
  }
  
  endShape();
}


```


le falta la f![image](https://github.com/user-attachments/assets/ad0f4831-7af9-4a4d-a041-3214878abe39)

uncion de poder usarlo dependiendo de la ubicacion del mouse 

con respecto al codigo original le podria añdir el

```js
function draw() {
  colorMode(HSB, 360, width, height);
  background(360, 0, height);

  var angleStep = 360 / segmentCount;

  beginShape(TRIANGLE_FAN);
  vertex(width / 2, height / 2);

  for (var angle = 0; angle <= 360; angle += angleStep) {
    var vx = width / 2 + cos(radians(angle)) * radius;
    var vy = height / 2 + sin(radians(angle)) * radius;
    vertex(vx, vy);
    fill(angle, mouseX, mouseY);
  }
```
ese seria el cambio a realizar
