![image](https://github.com/user-attachments/assets/64436973-d939-4ed7-8783-0e198534fc14)

La estructura del proyecto fue organizada para separar claramente los archivos del servidor y del cliente, además de incorporar recursos multimedia necesarios para la experiencia interactiva.

``html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Aplicación Interactiva p5.js</title>

  <!-- Librerías necesarias -->
  <script src="/socket.io/socket.io.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/addons/p5.sound.min.js"></script>
</head>
``
## sketch_host.js

``js
function setup() {
  createCanvas(800, 600);
  // Aquí se cargará y reproducirá la música de fondo
}

function draw() {
  background(30);
  // Visual opcional
}

function playMusic() {
  // Evitar múltiples instancias al reproducir
}

function pauseMusic() {
  // Pausar correctamente
}

``
## sketch_guest.js
``js
function setup() {
  createCanvas(800, 600);
  // Lógica para cargar video del usuario
}

function draw() {
  background(0);
  // Arte generativo dependiendo del video
}
``
## server.js
``js
const express = require('express');
const app = express();
const server = require('http').Server(app);
const io = require('socket.io')(server);

app.use(express.static('public'));

const PORT = process.env.PORT || 3000;
server.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});

let hostId = null;
let musicPlaying = false;

io.on('connection', (socket) => {
  if (!hostId) {
    hostId = socket.id;
    socket.emit('role', 'host');
  } else {
    socket.emit('role', 'guest');
    socket.emit('music-state', musicPlaying);
  }

  socket.on('disconnect', () => {
    if (socket.id === hostId) {
      hostId = null;
      const clients = io.sockets.sockets;
      clients.forEach((client) => {
        if (!hostId) {
          hostId = client.id;
          client.emit('role', 'host');
          client.emit('become-host');
        }
      });
    }
  });

  socket.on('music-play', () => {
    if (socket.id === hostId) {
      musicPlaying = true;
      socket.broadcast.emit('music-play');
    }
  });

  socket.on('music-pause', () => {
    if (socket.id === hostId) {
      musicPlaying = false;
      socket.broadcast.emit('music-pause');
    }
  });
});

``

✔️ Se abre index.html correctamente en el navegador.

✔️ El servidor (server.js) corre sin errores usando node server.js.

✔️ Se asigna el rol de host al primer cliente conectado y guest a los siguientes.

✔️ El host puede controlar la música con botones de reproducir y pausar.

✔️ Guests pueden seleccionar un video local y ver arte generativo basado en el mismo.

