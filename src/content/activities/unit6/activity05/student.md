Esta pieza generativa explora la relación simbiótica entre el cuerpo humano y lo digital, a través de una estética orgánico-digital. La app capta señales del cuerpo (movimiento, sonido, orientación) para transformar en tiempo real un paisaje visual proyectado, como si el usuario “habitara” un espacio virtual sensible a su presencia. Es una experiencia de inmersión donde el cuerpo y el entorno se influencian mutuamente, narrando una historia no lineal de conexión emocional y sensorial con lo virtual.


## Inputs

-Acelerómetro

Tipo: Coordenadas (x, y, z)

Rango: -1.0 a 1.0

Simulación: Sí (usando valores generados o movimientos predefinidos)

Relación con el storytelling: Representa el movimiento interno del cuerpo

-Micrófono

Tipo: Nivel sonoro

Rango: 0.0 a 1.0

Simulación: Sí (ruido generado)

Relación con el storytelling: Refleja la energía emocional

-Giroscopio

Tipo: Ángulo

Rango: 0° a 360°

Simulación: Sí (valores aleatorios o secuencias)

Relación con el storytelling: Cambia la perspectiva y equilibrio del entorno

-Control remoto (modo)

Tipo: Texto (modo predefinido)

Rango: “calma”, “caos”, etc.

Simulación: No (entrada directa desde interfaz)

Relación con el storytelling: Define el estado emocional global del sistema


## Proceso
Captura constante de inputs sensoriales.

Aceleración → distorsión visual de formas.

Nivel sonoro → intensidad de luces y vibraciones.

Ángulo → rotación y dirección del entorno visual.

Modo (calma/caos) → cambia el estilo general del algoritmo (colores, velocidad, complejidad).

Generatividad: Uso de ruido Perlin + variaciones aleatorias para crear sorpresa controlada.
Storytelling: Cada cambio en el cuerpo y entorno del usuario transforma la narrativa visual en tiempo real.
