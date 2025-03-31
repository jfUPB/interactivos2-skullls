¿Qué es WebRTC?

WebRTC (Web Real-Time Communication) es un conjunto de tecnologías y protocolos que permiten la comunicación en tiempo real entre navegadores y dispositivos sin necesidad de plugins o software adicional. Facilita la transmisión de audio, video y datos directamente entre pares (peer-to-peer), lo que lo hace ideal para aplicaciones de videollamadas, transmisión en vivo y colaboración en línea.

WebRTC utiliza una combinación de APIs y protocolos para establecer una conexión directa entre dispositivos. Su funcionamiento implica:

Descubrimiento e intercambio de información mediante un servidor de señalización (signaling server).

Establecimiento de la conexión usando el protocolo ICE (Interactive Connectivity Establishment) para encontrar la mejor ruta de comunicación entre los pares.

Intercambio de medios y datos a través de canales seguros.


Una peer connection es el enlace directo entre dos dispositivos que permite la transmisión de datos, audio y video en WebRTC. Se gestiona mediante la API RTCPeerConnection y utiliza diferentes protocolos para negociar la conexión, manejar flujos multimedia y asegurar una comunicación eficiente.

Un data channel es un canal de comunicación que permite el intercambio de datos arbitrarios entre pares utilizando el protocolo RTCDataChannel. Puede usarse para enviar mensajes, archivos y otros tipos de datos sin necesidad de una conexión de video o audio.

Un media stream es una secuencia de medios que puede contener múltiples pistas de audio y video. Se maneja mediante la API MediaStream, permitiendo capturar y transmitir contenido desde dispositivos como cámaras y micrófonos.

Un ICE server (Interactive Connectivity Establishment Server) ayuda a los dispositivos a descubrir la mejor ruta para establecer la conexión peer-to-peer, ya sea mediante STUN o TURN servers. WebRTC utiliza este mecanismo para sortear firewalls y NATs.

Un STUN server (Session Traversal Utilities for NAT) permite a los dispositivos determinar su dirección IP pública y la forma en que están conectados a Internet. Es útil para ayudar a establecer conexiones directas entre pares cuando están detrás de un NAT.

Un TURN server (Traversal Using Relays around NAT) actúa como un intermediario en caso de que una conexión directa entre pares no sea posible. En estos casos, retransmite la información, asegurando la comunicación pero con mayor latencia y consumo de recursos.

Un signaling server es un servidor que facilita el intercambio inicial de información entre pares para negociar la conexión WebRTC. Aunque WebRTC no define un protocolo específico para la señalización, comúnmente se usa WebSockets o HTTP para esta fase.

## Usos en la aplicacion que propuse

En la aplicación que propusimos previamente para la captura y transmisión de sonido entre clientes en GitHub Codespaces, los conceptos de WebRTC pueden implementarse de la siguiente manera:

Peer Connection: Se utilizaría para establecer la conexión entre los clientes sin necesidad de un servidor intermediario para la transferencia de datos de audio.

Data Channel: Si se necesita intercambiar metadatos o comandos adicionales durante la transmisión, se usará este canal.

Media Stream: Se empleará para capturar y transmitir el audio en tiempo real desde los micrófonos de los usuarios.

ICE Servers: Se configurarán STUN y TURN servers para garantizar que los dispositivos puedan conectarse incluso detrás de firewalls o NATs.

Signaling Server: Se utilizará para negociar la conexión inicial entre los clientes y facilitar el intercambio de credenciales ICE.
