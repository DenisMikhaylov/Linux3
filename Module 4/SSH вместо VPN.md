SSH вместо VPN (привязка к порту клиента)


windows desktop

Putty

Session
```
  HostNameIP 192.168.X.10
 ```
Connection->SSH->Tunnels
```
  Source port 3101
  Destination 192.168.100+X.101:3389
```
```
$ ssh -L 3101:192.168.100+X.101:3389 192.168.X.10
```
```
Remote Desktop Connection->127.0.0.1:3101
```
