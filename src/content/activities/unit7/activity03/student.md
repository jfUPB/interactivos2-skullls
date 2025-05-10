Configuración del servidor (server.js)
El servidor está configurado con Express y Socket.IO para escuchar conexiones de los clientes y gestionar roles de host y guest automáticamente.

![image](https://github.com/user-attachments/assets/5f2c27db-2465-4de3-8534-fcdb5ef9d9ad)

Código relevante del servidor
```js
const express = require('express');
const app = express();
const server = require('http').Server(app);
const io = require('socket.io')(server);

const PORT = process.env.PORT || 3000;
server.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});

app.use(express.static('public'));

let hostId = null;
let musicPlaying = false;

io.on('connection', (socket) => {
  console.log(`Cliente conectado: ${socket.id}`);
  
  if (!hostId) {
    hostId = socket.id;
    socket.emit('role', 'host');
  } else {
    socket.emit('role', 'guest');
    socket.emit('music-state', musicPlaying);
  }
  
  socket.on('disconnect', () => {
    console.log(`Cliente desconectado: ${socket.id}`);
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
      console.log('Música reproduciendo');
    }
  });

  socket.on('music-pause', () => {
    if (socket.id === hostId) {
      musicPlaying = false;
      socket.broadcast.emit('music-pause');
      console.log('Música pausada');
    }
  });
});
```
Configuración del cliente (sketch_host.js y sketch_guest.js)
Host (sketch_host.js)
El host carga una pista de música, la visualiza con p5.js y controla la reproducción/pausa.

Funciones clave para enviar mensajes al servidor:

```js
sketch.playMusic = function() {
  if (backgroundMusic && backgroundMusic.isLoaded()) {
    if (!isPlaying) {
      backgroundMusic.play();
      isPlaying = true;
      socket.emit('music-play');  // Enviar mensaje al servidor
    }
  }
};

sketch.pauseMusic = function() {
  if (backgroundMusic && backgroundMusic.isLoaded() && isPlaying) {
    backgroundMusic.pause();
    isPlaying = false;
    socket.emit('music-pause');  // Enviar mensaje al servidor
  }
};
Conexión a Socket.IO y recepción de mensajes:


const socket = io();

socket.on('role', (role) => {
  console.log('Mi rol es:', role);
});

socket.on('music-play', () => {
  sketch.playMusic();
  console.log('Recibido: reproducir música');
});

socket.on('music-pause', () => {
  sketch.pauseMusic();
  console.log('Recibido: pausar música');
});
```

Guest (sketch_guest.js)
El guest no controla la música, solo visualiza el arte generativo sincronizado al estado de la música.

Conexión a Socket.IO y recepción de mensajes:

```js
const socket = io();

socket.on('role', (role) => {
  console.log('Mi rol es:', role);
});

socket.on('music-play', () => {
  sketch.musicStateChanged(true);
  console.log('Recibido: reproducir música');
});

socket.on('music-pause', () => {
  sketch.musicStateChanged(false);
  console.log('Recibido: pausar música');
});

socket.on('music-state', (isPlaying) => {
  sketch.musicStateChanged(isPlaying);
  console.log('Estado inicial de música:', isPlaying);
});
```
Flujo de comunicación establecido
Un cliente se conecta.
 a. Si es el primero, el servidor lo designa como host.
 b. Si es posterior, el servidor lo designa como guest y le envía el estado actual de la música.

Cuando el host reproduce o pausa la música:
 a. Envía music-play o music-pause al servidor con socket.emit().
 b. El servidor propaga el mensaje a todos los guests con socket.broadcast.emit().
 c. Los guests actualizan su estado visual según el mensaje recibido.

Si el host se desconecta, el servidor designa automáticamente un nuevo host entre los clientes restantes.
