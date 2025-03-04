![image](https://github.com/user-attachments/assets/6940730c-7977-4189-b296-8a27c566b3db)
```js
function setup() {
  createCanvas(600, 400);
  noLoop(); 

}

function draw() {
  background(220);
  
  for (let i = 0; i < 10; i++) { 
    let shapeType = int(random(3)); 
    let x = random(width);
    let y = random(height);
    let size = random(30, 80);
    let col = color(random(255), random(255), random(255));
    fill(col);
    noStroke();
    
    if (shapeType === 0) {
      ellipse(x, y, size, size);
    } else if (shapeType === 1) {
      rect(x, y, size, size);
    } else {
      triangle(x, y, x + size, y, x + size / 2, y - size);
    }
  }
}
```
