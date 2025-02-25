![image](https://github.com/user-attachments/assets/63401c97-2adf-4869-91ae-11ad5742feae)

Con ayuda de varios videos pude construir un codigo que puedea ajustar el color de los pixeles y la transparencia de la imagen que yo le de, esto con la funcion de llamar a una imagen y recolectar la info de los pixeles originales 

```js
let img;

function preload() {
  img = loadImage('2.jpeg'); // para agregar la imagen Importante colocar la imagen en la carpeta y el nombre identico
}

function setup() {
  createCanvas(img.width, img.height);
  img.loadPixels();
  
  for (let y = 0; y < img.height; y++) {
    for (let x = 0; x < img.width; x++) {
      let index = (x + y * img.width) * 4;
      
     // aqui estan los colores de la imagen OG
      let r = img.pixels[index + 0];
      let g = img.pixels[index + 1];
      let b = img.pixels[index + 2];
      
      // Aplica una transformación basada en la posición
      let brillo = (r + g + b) / 3;
      let factor = map(y, 0, img.height, 0.5, 1.5);
      
      img.pixels[index + 0] = r * factor; // Con esto aumento el valor de rojo
      img.pixels[index + 1] = g * random(0.8, 1.2); // verde random
      img.pixels[index + 2] = b * sin(x * 0.01) * 2; // azul pero con una funcon de sen
      
      
      img.pixels[index + 3] = map(y, 0, img.height, 255, 100);
    }
  }
  
  img.updatePixels();
}

function draw() {
  background(0);
  image(img, 0, 0);
}
```
