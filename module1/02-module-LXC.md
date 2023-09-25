LXC

Подготовка родительской (host) системы

root@server:~# apt install bridge-utils

root@server:~# nano /etc/network/interfaces

добавить в конец

auto br0
iface br0 inet static
        address 192.168.X.10
        netmask 255.255.255.0
        gateway 192.168.X.1
        bridge_ports eth0


root@server:~# init 0
Для режима bridge в lxc понадобиться включить «неразборчивый режим» в адаптере

Установка и настройка lxc

root@server:~# apt install lxc

настройка

root@server:~# nano /etc/default/lxc

#[ ! -f /etc/default/lxc-net ] || . /etc/default/lxc-net

Создание ветки дочерней системы

# lxc-create -t debian -n www

Установка ПО в дочерней системе

root@server:~# cp /etc/ssh/sshd_config /var/lib/lxc/www/rootfs/etc/ssh/sshd_config

root@server:~# cp /etc/resolv.conf /var/lib/lxc/www/rootfs/etc/resolv.conf

root@server:~# chroot /var/lib/lxc/www/rootfs /bin/bash

root@server:/# PS1='www:\w# '

www:/# apt purge isc-dhcp-client

www:/# apt install nano vim iputils-ping

Настойка сетевых параметров дочерней системы

www:/# cat /etc/hosts

127.0.0.1       localhost

192.168.X.20    www.corp

Управление учетными записями в дочерней системе

www:/# passwd
... 123

www:/# exit

Настройка lxc для запуска дочерней системы в контейнере

root@server:~# nano /var/lib/lxc/www/config

lxc.net.0.type = veth
lxc.net.0.link = br0
lxc.net.0.flags = up
lxc.net.0.ipv4.address = 192.168.X.20/24
lxc.net.0.ipv4.gateway = 192.168.X.1
lxc.start.auto = 1

root@server:~# lxc-ls -f

Запуск/мониторинг/остановка контейнера

root@server:~# lxc-start -n www 

root@server:~# lxc-info -n www

root@server:~# lxc-attach -n www -- ps ax

root@server:~# lxc-attach -n www -- /bin/bash

root@server:~# ssh 192.168.X.20

root@server:~# lxc-stop -n www

root@server:~# systemctl start lxc@www

root@server:~# systemctl stop lxc@www
