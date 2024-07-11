HTTP (Hypertext Transfer Protocol) es el protocolo de comunicación utilizado para la transferencia de información en la World Wide Web. Es un protocolo de aplicación, lo que significa que facilita la comunicación entre los clientes (como navegadores web) y los servidores web. HTTP sigue un modelo cliente-servidor, donde el cliente envía una solicitud al servidor y espera una respuesta.

Aquí hay algunos puntos clave sobre HTTP:

1. ***Petición-Respuesta***: El cliente envía una solicitud HTTP al servidor para obtener recursos, como páginas web, imágenes, archivos, etc. El servidor procesa la solicitud y envía una respuesta HTTP que contiene el recurso solicitado o un código de estado que indica el resultado de la solicitud.
2. ***Protocolo sin estado***: HTTP es un protocolo sin estado, lo que significa que cada solicitud y respuesta son independientes entre sí. El servidor no mantiene información sobre el estado de las solicitudes anteriores, lo que simplifica la implementación y la escalabilidad del protocolo.
3. ***Basado en texto***: Las solicitudes y respuestas HTTP están formateadas en texto legible por humanos, lo que facilita la depuración y el análisis. Están compuestas por líneas de encabezado seguidas opcionalmente por un cuerpo de mensaje que puede contener datos adicionales, como el contenido de una página web.
4. ***Puerto estándar***: Por lo general, HTTP utiliza el [[puerto]] TCP 80 para la comunicación, aunque también se pueden usar otros puertos (por ejemplo, 8080) dependiendo de la configuración del servidor.
5. ***Protocolo no seguro***: HTTP no proporciona cifrado de datos de forma predeterminada, lo que significa que la información transmitida a través de HTTP no está protegida y pued e ser interceptada y leída por terceros. Para mejorar la seguridad, se utiliza HTTPS (HTTP Secure), que utiliza SSL/TLS para cifrar la comunicación.

La capa de aplicación es la séptima capa del [[modelo OSI]] y es responsable de proporcionar servicios de red a las aplicaciones de usuario final. Esta capa se encarga de la comunicación entre las aplicaciones de usuario y los servicios de red subyacentes.

Procedimiento de enumeración:
- Tecnologías de la web: ```whatweb 127.0.0.1```