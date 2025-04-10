## Storytelling
Esta pieza generativa explora la relación simbiótica entre el cuerpo humano y lo digital, a través de una estética orgánico-digital. La app capta señales del cuerpo (movimiento, sonido, orientación) para transformar en tiempo real un paisaje visual proyectado, como si el usuario “habitara” un espacio virtual sensible a su presencia. Es una experiencia de inmersión donde el cuerpo y el entorno se influencian mutuamente, narrando una historia no lineal de conexión emocional y sensorial con lo virtual.

Antes
![image](https://github.com/user-attachments/assets/5cfcf5d2-4b15-4198-ac6e-8720ab06f351) 

Despues 
![image](https://github.com/user-attachments/assets/0bdae322-c25d-4c62-8410-534fe723fefd)

El por que de cada cosa

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

-Camara

Tipo: Bits

Simulación: no

Relación con el storytelling: PArte esecial donde puedes conectar con la experiencia 

-Control remoto (modo)

Tipo: Texto (modo predefinido)

Rango: “calma”, “caos”, etc.

Simulación: No (entrada directa desde interfaz)

Relación con el storytelling: Define el estado emocional global del sistema


## Proceso
Captura constante de inputs sensoriales.

Aceleración → distorsión visual de formas.

Nivel sonoro → intensidad de luces y vibraciones.

Modo (calma/caos) → cambia el estilo general del algoritmo (colores, velocidad, complejidad).

Generatividad: Uso de ruido Perlin + variaciones aleatorias para crear sorpresa controlada.
Storytelling: Cada cambio en el cuerpo y entorno del usuario transforma la narrativa visual en tiempo real.

## Outputs

Tipo: Visual generativo interactivo (pensado para proyección grande o instalación inmersiva).

Elementos generados: Formas líquidas, patrones biomórficos, líneas pulsantes, nubes digitales, etc.

Propiedades dinámicas: Color, tamaño, rotación, frecuencia, densidad y complejidad.

Relación Input → Process → Output:
Movimiento del cuerpo (acelerómetro) → distorsiona el mundo como si “respirara”.

Voz o sonido (micrófono) → ilumina o fragmenta el entorno, como una expresión emocional.

Giro del celular (giroscopio) → altera el punto de vista, como si cambiaras de dimensión.

Modo seleccionado → controla la atmósfera general (paz, agitación, introspección, expansión...).
