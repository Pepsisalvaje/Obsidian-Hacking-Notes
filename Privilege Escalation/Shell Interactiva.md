## Python 

```python3 -c 'import pty;pty.spawn("/bin/bash")'```
Presionas ctrl + z
```stty raw -echo;fg```
presionas enter dos veces
```export TERM=xterm```

## Bash

```script /dev/null -c bash```
presionar ctrl+z
```stty raw -echo;fg```
presionar enter dos veces
```reset xterm```
```stty rows 62 columns 248```
```export TERM=xterm SHELL=bash```
