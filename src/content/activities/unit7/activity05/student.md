## Pruebas sistemáticas realizadas

Basado en mis escenarios "¿Qué pasaría si?" de la Unidad 6, realicé las siguientes pruebas:

- ¿Qué pasa si se carga un video muy grande o con resolución alta?  
- ¿Qué pasa si se maximizan todos los sliders (brillo e intensidad) al mismo tiempo?  
- ¿Qué pasa si el host pausa/reproduce la música rápidamente varias veces?  
- ¿Qué ocurre si un guest se conecta después de que el host haya empezado la música?

---

## Error significativo encontrado

### Descripción del error

Durante las pruebas, detecté que las partículas del sistema visual (en el guest) **no se sincronizaban adecuadamente al ritmo de la música**.  
Aunque la música se reproducía correctamente, la cantidad e intensidad de las partículas no respondían dinámicamente a los cambios sonoros como estaba previsto.  
Esto hacía que la visualización pareciera desconectada del estímulo auditivo.

---

## Identificación de la causa

Utilicé `console.log()` para verificar los valores de energía del espectro (bass y lowMid) y confirmé que esos valores se calculaban correctamente en el host, pero **no se estaban enviando ni recibiendo por red** hacia los guests.

El sistema de partículas del guest dependía solo de un estado binario (música activa o pausada) y no estaba recibiendo datos más precisos del análisis del audio (por ejemplo, la intensidad de bajos).  
Esto limitaba la capacidad de sincronización precisa.

---

## Corrección realizada

### Enfoque de solución

Decidí **enviar periódicamente (desde el host al guest)** un mensaje con la intensidad de bajos (`bassEnergy`) calculada con p5.FFT.  
Esto permitiría que el guest ajustara dinámicamente el comportamiento de las partículas en función de ese valor.

### Fragmento de código añadido en el host

```javascript
setInterval(() => {
  const bass = fft.getEnergy("bass");
  socket.emit('bass-energy', bass);
}, 100); // cada 100 ms
socket.on('bass-energy', (bassValue) => {
  // Mapear valor de bajos (0-255) a un rango útil para partículas
  const intensityFactor = map(bassValue, 0, 255, 0.5, 2.0);
  particleSystem.adjustIntensity(intensityFactor);
});
```
Refinamiento estético realizado
Descripción
Aprovechando esta mejora, refiné también la escala de colores de las partículas para que cuando la intensidad de bajos fuera alta, los colores viraran hacia tonos más cálidos (rojos/naranjas), y cuando fuera baja, hacia tonos fríos (azules).
Esto añadía un nivel visual adicional para reforzar la relación sonido-imagen.

Conclusión
Realicé un ciclo completo de prueba, identificación, corrección y refinamiento, mejorando tanto la robustez funcional como la estética visual del prototipo.
El prototipo actualizado ahora sincroniza correctamente la visualización de partículas con la intensidad de la música, generando una experiencia audiovisual más coherente e inmersiva.
