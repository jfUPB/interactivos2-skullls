Para esta entrega estuve jugando con el codespaces, pero he tenido varios problemas aunque esto me ha permitido entender como funciona las conexiones entre servidor cliente, primero mostare como quede mi aplicacion

![image](https://github.com/user-attachments/assets/be18a08b-92fa-486b-94dc-137374a5a30d)

tenemos una interfaz basica para mostrar las utilidades, en esta se pueden tomar y cargar fotos, aunque no he logrado que se muestren

Por la parte de los codigos tenemos varios camhbios, lo hice con ayuda de chat gpt, pero me limite a darle problemas muy puntuales

```js
///// SERVIDOR (server.js) /////

const express = require("express");
const http = require("http");
const { Server } = require("socket.io");

const app = express();
const server = http.createServer(app);
const io = new Server(server);

app.use(express.static("public")); // Sirve archivos estáticos desde "public"

io.on("connection", (socket) => {
    console.log("Un usuario se ha conectado", socket.id);
    
    // Recibir mensaje de un cliente y enviarlo a todos
    socket.on("send-message", (data) => {
        io.emit("receive-message", data); // Reenvía a todos los clientes
    });

    // Recibir imagen y enviarla a otros clientes
    socket.on("send-image", (data) => {
        socket.broadcast.emit("receive-image", data); // Solo a otros clientes
    });

    socket.on("disconnect", () => {
        console.log("Un usuario se ha desconectado", socket.id);
    });
});

server.listen(3000, () => {
    console.log("Servidor corriendo en http://localhost:3000");
});

///// CLIENTE DESKTOP (public/desktop/sketch.js) /////

let socket;

function setup() {
    createCanvas(600, 400);
    background(200);
    socket = io();

    socket.on("receive-message", (data) => {
        console.log("Mensaje recibido:", data);
    });

    socket.on("receive-image", (data) => {
        let receivedImage = createImg(data.image, "received image");
        receivedImage.position(10, 10);
        receivedImage.size(100, 100);
    });
}

function mousePressed() {
    let data = { message: "Hola desde desktop!" };
    socket.emit("send-message", data);
}

///// CLIENTE MOBILE (public/mobile/sketch.js) /////

let socket;

function setup() {
    createCanvas(windowWidth, windowHeight);
    background(220);
    socket = io();

    socket.on("receive-message", (data) => {
        console.log("Mensaje recibido en móvil:", data);
    });
}

function touchStarted() {
    let data = { message: "Hola desde el móvil!" };
    socket.emit("send-message", data);
}
```
Explicacion

1. ¿Cómo se comunican los clientes con el servidor?
esto se hace a traves dewebsockets, usando socket.io, cuando el cliente se conecta se registra en el servidor ( io.on(conection)) los clientes mandan mensajes con un socket.emit y el server lo reenvia con un io.emit

2. ¿Cómo se comunican los clientes entre sí?
