El modelo OSI se divide en 7 capas específicas:
1. Física: Especifica los dispositivos para que los datos se transmitan por estos medios y sean procesados en la siguiente capa.
2. Enlace: Es el encargado de observa el paquete para poder validar si tiene algún defecto en su formato y controla el flujo con el que se envían los paquetes.
3. Red: Se encarga del direccionamiento [[IP]] origen y destino. Prioriza paquetes y decide que ruta utilizar para enviar los datos.
4. Transporte: Es el encargado de garantizar el envío y recepción de los paquetes. Aquí actúa el protocolo TCP y UDP.
5. Sesión: Esta capa se encarga de establecer y terminar la conexión entre hosts. Aquí se encuentran los logs de eventos
6. Presentación: Traduce los paquetes para que la capa 7 pueda utilizarlos. Se encarga de la conversión de códigos a caracteres y cifrado.
7. Aplicación: Consume los datos de la capa 6 y se lo muestra a la [[IP]] destino.