# 🧠 Bitácora – Actividad 02: Implementando el núcleo del proceso y la simulación

## 🔄 Lógica del Proceso

El núcleo del sistema es un motor de arte generativo que:
- Analiza cuadro a cuadro el video cargado por el usuario.
- Usa los colores y posiciones de píxeles del video para generar partículas animadas.
- Controla visualmente la cantidad, color y brillo de las partículas a través de sliders en la interfaz.

El archivo clave es `sketch_guest.js`, y en la clase `ParticleSystem`, el método `update()` implementa el algoritmo principal:

```js
const intensity = window.sketchConfig.intensityValue / 100;
const particleGenCount = Math.floor(5 * intensity);

for (let i = 0; i < particleGenCount; i++) {
  if (this.particles.length < this.maxParticles * intensity) {
    // Crear partículas basadas en píxeles del video
    ...
  }
```

La simulación de datos se hace mediante sliders que simulan inputs en tiempo real:

Intensidad del efecto (intensityValue)

Límite de colores (colorLimitValue)

Brillo de las partículas (brightnessValue)

En el sketch, estos valores se actualizan cada frame:

```js
function updateFromSliders() {
  particleSystem.adjustBrightness(window.sketchConfig.brightnessValue);
}
```

Conexión entre Simulación y Proceso
La lógica generativa lee directamente los datos simulados para alterar su comportamiento:

intensityValue controla cuántas partículas se generan.

colorLimitValue determina si se reduce la gama de colores.

brightnessValue controla cuán luminosas son las partículas renderizadas.

Esto ocurre durante la ejecución de:

```js
particleSystem.update(videoGraphics);
particleSystem.display();
```

Durante la ejecución se usan console.log() para verificar funcionamiento:
```js
console.log('Cargando video:', file.name);
console.log('Video listo para reproducirse');
console.log('Video reproduciendo');
```

Reto
Autoplay bloqueado por navegador	Se implementó reproducción condicional y advertencias al usuario.
Sobrepoblación de partículas	Se ajustó maxParticles dinámicamente según la intensidad.
Reducción controlada de color	Se desarrolló applyColorLimit() con interpolación entre paleta predefinida y color real.
