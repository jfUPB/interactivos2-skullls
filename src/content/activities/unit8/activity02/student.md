VisualSync – Arte generativo a partir de música y video

⸻

Introducción breve

Este proyecto es una aplicación interactiva que transforma videos enviados por los usuarios en composiciones visuales generativas. A partir de las propiedades del video y el sonido, se crean visuales únicos que reaccionan en tiempo real, combinando arte y tecnología en una experiencia audiovisual.

⸻

Concepto y narrativa

La idea nace del interés por fusionar música y arte visual de una forma personalizada. En lugar de generar visuales genéricos, esta app toma el video del cliente como punto de partida, y lo convierte en una pieza de arte visual donde cada sonido y movimiento tiene una reacción.

El proyecto busca explorar cómo los datos invisibles de un video (como la intensidad o el brillo) pueden ser usados como materia prima para crear experiencias visuales únicas.

⸻

Diseño técnico – Modelo IPO

Inputs
	•	Intensidad: qué tan fuerte suena la música
	•	Posición: dónde están los elementos en el video
	•	Brillo: nivel de iluminación del video
	•	Video: archivo que manda el cliente

Proceso
	•	Análisis en tiempo real de los valores de audio y video
	•	Generación visual usando técnicas de arte generativo
	•	Composición audiovisual sincronizada con los datos recibidos

Outputs
	•	Video final: el resultado visual generado con base en los inputs
	•	Sonido: el audio original o modificado, acompañando los visuales

⸻

Video demostrativo

[Video embebido aquí]
Este será el video donde se muestre el prototipo en acción.

⸻

Tecnologías utilizadas
	•	p5.js: para generar las visuales interactivas
	•	JavaScript: lógica del programa y manejo de inputs
	•	HTML/CSS: estructura básica del entorno de la app
	•	Herramientas de edición: para el montaje y limpieza del video final

⸻

Tutorial paso a paso para reproducir el proyecto
	1.	Abrí el entorno de desarrollo (p5.js o un editor como Visual Studio Code).
	2.	Copiá el código del proyecto en el archivo principal sketch.js.
	3.	Subí un video de prueba con sonido, o cargá uno desde el código.
	4.	El sistema analizará automáticamente los datos del video (brillo, posición, volumen).
	5.	Observá cómo se generan los visuales en tiempo real sobre el video.
	6.	Exportá el resultado si querés guardarlo como pieza final