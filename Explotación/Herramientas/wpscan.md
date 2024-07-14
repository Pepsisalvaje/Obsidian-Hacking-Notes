First scan with the following command to retrieve all general information.

```
wpscan --url http://127.0.0.1
```

When we discover the basic information depend on your need.

- To discover all user:
```
wpscan --url http://127.0.0.1 -e u
```

- To do bruteforce:
```
wpscan --url http://wordpress.com -U usuario1 -P pass.txt
```

- - To check all plugins (this is necessary so yo can check all the information of the wordpress and find on your own if there's a specific vuln):
```
wpscan --url https://wordpress.com -e vp
```

- To check plugins vulnerabilities:
```
wpscan --url https://wordpress.com -e vp
```

- To check themes vulnerabilities:
```
wpscan --url https://wordpress.com -e vp
```