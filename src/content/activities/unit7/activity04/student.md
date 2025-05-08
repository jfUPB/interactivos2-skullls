## Inputs implementados

- **Inputs directos (cliente Guest)**  
  - Sliders de brillo (`brightnessValue`) y color (`colorLimitValue`)  
  - Selección de video desde archivo  
  - Clicks para reproducir/pausar video

- **Inputs de red (host y guest)**  
  - Mensajes `music-play` y `music-pause` desde Socket.IO

- **Inputs directos (cliente Host)**  
  - Clic en botones (o interfaz) para reproducir o pausar música

---

 Fragmentos de código relevantes

A. Inputs → Proceso (Guest)

Sliders afectan el sistema de partículas

```javascript
function updateFromSliders() {
  // Brillo del sistema de partículas ajustado con slider
  particleSystem.adjustBrightness(window.sketchConfig.brightnessValue);
}
socket.on('music-play', () => {
  sketch.musicStateChanged(true);
});

socket.on('music-pause', () => {
  sketch.musicStateChanged(false);
});

sketch.musicStateChanged = function(isPlaying) {
  musicPlaying = isPlaying;
  if (musicPlaying) {
    particleSystem.maxParticles = 500;
  } else {
    particleSystem.maxParticles = 300;
  }
};
```
B. Proceso → Outputs (Guest)
1️Generación de partículas en base a video y estado interno

```javascript
particleSystem.update(videoGraphics);
particleSystem.display();
```
Visualización de estado de música (texto dinámico)

```javascript
sketch.text(musicPlaying ? "♪ Música Activa ♪" : "Música Pausada", sketch.width - 80, 20);
A. Inputs → Proceso (Host)
```
Clics para reproducir/pausar música y emitir mensaje de red

```javascript
sketch.playMusic = function() {
  backgroundMusic.play();
  isPlaying = true;
  socket.emit('music-play');
};

sketch.pauseMusic = function() {
  backgroundMusic.pause();
  isPlaying = false;
  socket.emit('music-pause');
};
```
B. Proceso → Outputs (Host)
Visualización de forma de onda de la música

```javascript

const waveform = fft.waveform();
sketch.drawWaveform(waveform);
```
Círculos reactivos a frecuencias bajas

```javascript
const spectrum = fft.analyze();
sketch.drawBassCircles(spectrum);
```
Texto de estado de música (visual)

```javascript
sketch.text(isPlaying ? "Música Reproduciendo" : "Música Pausada", sketch.width/2, 30);
```
 Flujo IPO integrado
Input	Proceso	Output
Sliders (guest)	Modifican brillo/intensidad partículas	Cambio en cantidad y brillo de partículas
Selección video (guest)	Procesamiento video en partículas	Partículas reflejan video
Clic reproducir/pausar (host)	Música se reproduce/pausa + envío de mensaje	Visualización de onda/círculos + texto
Mensaje de red (music-play/pause)	Cambia estado de música en guest	Aumenta/disminuye partículas + texto "Música Activa/Pausada"
