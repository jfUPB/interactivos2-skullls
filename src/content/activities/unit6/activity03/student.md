1. Inputs extremos
Escenario: El usuario genera un nivel de sonido altísimo (más de 90 dB) y simultáneamente mueve mucho el dispositivo (valores acelerómetros cercanos a 1.0).
El brillo y la saturación de los visuales aumentan al máximo, generando una imagen intensa, vibrante y posiblemente caótica.

Este comportamiento es interesante y puede funcionar como un “clímax” visual, pero podría volverse excesivo o molesto. Se podria limitar los parametros a unos recomendados, para generar imagnes claras

3. Cambio de parámetro interno
Escenario: Duplicar la sensibilidad a los movimientos.
Pequeños movimientos del dispositivo generarían reacciones visuales muy pronunciadas, la experiencia se vuelve más reactiva y quizás menos controlable.

Podría ser útil para usuarios que no desean moverse mucho o en contextos de baja interacción física, pero puede también romper la sensación fluida si todo reacciona de forma exagerada. Sería ideal ofrecer un modo de “sensibilidad ajustable”.

3. Combinación de inputs
Escenario: Alto movimiento + comando remoto “modo calma” activado.
El algoritmo estaría recibiendo inputs contradictorios: movimiento intenso pide distorsión, pero el modo calma quiere visuales suaves.

Este tipo de contradicción es muy interesante. Puede aprovecharse como una “colisión de estados” que genere visuales intermedios o híbridos.

4. Falla de input
Escenario: El sensor de sonido deja de enviar datos (ej. error de micrófono o interrupción).
Si no se prevé, los visuales dejarán de reaccionar al audio o se congelarán.

Idealmente, el algoritmo debe asumir un valor neutro o simulado mientras se reestablece el input, es crucial tener un sistema de fallback o valor por defecto para mantener la experiencia continua. Este tipo de interrupciones no deben dañar la narrativa ni desconectar al usuario del flujo visual.

