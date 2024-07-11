Es una herramienta para fuzzear como [[ffuf]]

Su funcionamiento es básico pero depende de lo que se requiera fuzzear.

En el siguiente ejemplo se muestra como se utiliza para fuzzear un servicio [[ftp]]:

```hydra -l user -P passlist.txt ftp://10.10.15.223 -t 64 -F```

Si se quiere realizar fuerza bruta a un servicio [[ssh]] es necesario el siguiente comando (-t hace referencia al número de hilos):

```hydra -l root -P passlist.txt 10.10.15.223 -t 4 ssh```

## Login Form

También si se quiere realizar fuerza bruta a un formulario se puede realizar de las dos siguientes formas siendo la primera en el puerto por defecto que te brinda la web o la segunda en un puerto en específico:

Es importante también revisar si es un http-post-form, https-post-form, etc en la inspección de la web.

```sudo hydra -l <USER> -P <WORDLIST> 10.10.15.223 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V```

```
hydra -l admin -P /home/quino/Maquinas_hack/Dockerlabs.es/Strongjenkins/dict.txt 172.17.0.2 -s 8080 http-post-form "/j_spring_security_check:j_username=^USER^&j_password=^PASS^&from=%2F&Submit=Login:Invalid username or password" -v
```

- /: Hace referencia en que página se encuentra el login form.
- username: el campo (dentro del html) donde se ingresará el usuario.
- ^USER^: Hace referencia al valor que se le asignará.
- password:  el campo (dentro del html) donde se ingresará el usuario.
- ^PASS^: Hace referencia al valor que se le asignará.
- F=incorrect: Es la sentencia que entregará el servidor cuando el formulario falle

Si se tiene alguna duda consultar la siguiente web para fuerza bruta de login forms:

https://www.manrajbansal.com/post/how-to-use-hydra-to-brute-force-login-forms