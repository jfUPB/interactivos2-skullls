# VisualSync – Arte generativo en colaboración audiovisual

**VisualSync** es una aplicación interactiva web que genera visuales en tiempo real a partir de un video cargado por el usuario y una pista musical reproducida por otro. Utiliza tecnologías como p5.js y Socket.IO para crear una experiencia audiovisual colaborativa y única.

---

## 🎨 Descripción

Este proyecto permite a varios usuarios conectarse: uno actúa como **host** y reproduce música, mientras los demás actúan como **guests**, cargando videos que se transforman en visuales generativos.

Las partículas visuales reaccionan al ritmo de la música y a los datos del video (color, brillo, movimiento), creando composiciones en vivo.

---

## Tutorial de reproducción

### Prerrequisitos

Asegurate de tener instalado:

- [Node.js](https://nodejs.org/) (versión 14 o superior)
- Navegador web moderno (Chrome o Firefox recomendado)
- (Opcional) Visual Studio Code u otro editor de código

### Instalación

1. Cloná este repositorio o descargá los archivos.

2. Abrí una terminal y navegá a la carpeta del proyecto:

```bash
cd visualsync
```
3 Instalá las dependencias:
```bash
npm install
```

## Ejecución
Iniciá el servidor:
```
npm run dev
```

Abrí tu navegador y entrá a:
http://localhost:3000
Esta pestaña actuará como host (control de música).


Abrí otra pestaña o navegador y accedé a la misma URL:
http://localhost:3000
Esta será la sesión del guest.

En el guest, subí un video y hacé clic en "Reproducir video". En el host, dale a "Reproducir" para iniciar la música.

Ajustá los sliders de intensidad, brillo y color para modificar la experiencia visual.


Tecnologías utilizadas
p5.js – Visuales, animación, video y audio

p5.sound – Análisis FFT

Socket.IO – Comunicación en tiempo real

Node.js + Express – Backend y servidor local

HTML, CSS, JavaScript – Interfaz y lógica de usuario

Demo


https://github.com/user-attachments/assets/99a8b009-c4af-4f57-b021-149674806bde



Reflexión
Este proyecto nació como un experimento de colaboración creativa entre sonido e imagen. Me permitió aprender a combinar análisis de audio, manipulación de video y programación interactiva en red. Lo veo como una base sólida para futuros proyectos de arte generativo, instalaciones interactivas o presentaciones en vivo.




