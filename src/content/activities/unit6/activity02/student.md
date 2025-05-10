-1. Que inputs uso

-Sensor de movimiento que trace valores en x, y y z estos tienen como mision seguir el movimiento y la fluiez del usuario, para generar los visuales y cambiar un poco el sonido de la musica, volviendola mas brillante o mas apgado
-Microfonos del celular, medimos por db el sonido y puedo coger la api de algun programa para cancelacion de ruido de fondo que para cuando empieces a hablar se puedan proyectar en la pantalla
-Camara del celular tomamos la imagen que nos esta reflejando, esto nos daria datos en binarios y se proyectara tu cara en los visuales.

En medidas de tiempo p´rentendo cambiar de dispusitivo maestrro cada 2 minutos, activandose la funcion de poder usar las caracteristricas de tu celular, la idea es que varios dispositivos se puedan conectar a la vez, cambiando de usuario en usuario

2. algoritmos

-recibir los datos de los sensores en tiempo real, los interpreta dependiento de sus valores y los convierte en informacion visual.
-Se promedia los sonidos y se reducen para no saturar y desbalancear el orden de los sonidos
-generar proyecciones a travez de los datos de la camara
-los movimientos del usuario generar disucion en la imagen y rayos de luz diferentes en cada espacio

3. Outputs

-figuras en las proyecciones, que cambian a medida que el usuario cambie su movimiento facial
-Sonoramente se generan espacios de tension dependiento, de la emocion de los usuarios 


hsb

1. Inputs
Fuente	Tipo de Dato	Rango/Formato	Simulación	Conexión con Storytelling
Sensor de movimiento (acelerómetro)	Número	Valores X, Y, Z en rango -1.0 a 1.0	Sí, con valores predefinidos	Representa los movimientos del usuario que afectan la fluidez de los visuales.
Micrófono del celular	Número (nivel de sonido)	0 - 100 dB	Sí, con valores simulados	Refleja la intensidad del sonido del público en cambios de luz o textura.
Control remoto (app en otro dispositivo)	Texto/Booleano	Comandos predefinidos ("pausa", "reiniciar", "modoA")	No	Permite modificar la experiencia en tiempo real según las necesidades del evento.
API de música (opcional)	Número/Categoría	BPM, tonalidad, energía de la canción	Sí, con datos simulados	Sincroniza los visuales con la música para reforzar la conexión humano-digital.
2. Proceso (Algoritmo)
Descripción textual
Se reciben los datos del sensor de movimiento y del micrófono en tiempo real.

Se normalizan los valores para evitar cambios bruscos o inconsistencias.

El nivel de sonido controla la intensidad de los efectos visuales (ejemplo: mayor volumen → mayor brillo y saturación).

Los movimientos del usuario afectan la distorsión y fluidez de los gráficos proyectados.

Si el control remoto envía comandos, el sistema responde con cambios en la dinámica de los visuales (pausar, alterar efectos, cambiar estilos).

(Opcional) Si hay datos musicales, la velocidad y tonalidad influyen en la generación de patrones visuales.

Se genera y proyecta la imagen basada en las transformaciones anteriores.

Pseudocódigo
plaintext
Copiar
Editar
Si sensor_movimiento cambia entonces
   modificar_forma(velocidad = X, dirección = Y, intensidad = Z)

Si nivel_sonido > umbral_alto entonces
   aumentar_brillo_y_saturación()

Si comando_remoto == "pausa" entonces
   detener_animación()

Si API_musica.activa entonces
   sincronizar_bpm_con_patrón_visual()
3. Outputs
Tipo	Elementos Generados	Propiedades Dinámicas	Relación Input -> Process -> Output	Conexión con Storytelling
Visual	Figuras orgánicas y dinámicas	Tamaño, fluidez, color, brillo	Movimiento → distorsión, Sonido → intensidad de luz	Representa la interacción humano-digital como algo vivo.
Sonoro (Opcional)	Modulación de audio ambiental	Volumen, reverb	Nivel de sonido → cambios en la atmósfera sonora	Expresa la fusión entre lo físico y lo digital.
