Поиск посторонних DHCP серверов
```
# wget http://www.netpatch.ru/projects/dhcdrop/dhcdrop-lin-0.5.tar.bz2

# tar -xvf /root/dhcdrop-lin-0.5.tar.bz2 -C /usr/local/sbin/ dhcdrop
```

Запуск

```
# /usr/local/sbin/dhcdrop -b -i eth0 -c 2 -y
```
```
# /usr/local/sbin/dhcdrop -t -b -q -i <intface> -l <mac_address> > /tmp/dhcp.txt || (cat /tmp/dhcp.txt | mail -s 'Critical. Second DHCP.' root@corpX.un)
```
