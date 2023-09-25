Управление учетными записями в Linux
Просмотр базы данных пользователей и групп
```
$ cat /etc/passwd

# cat /etc/shadow

$ cat /etc/group
```

Добавление учетной записи
```
# useradd -u 10001 -m -s /bin/bash user1

# cat /etc/default/useradd
```

Добавление групп

```
# groupadd -g 15001 group1
# groupadd -g 15002 group2
```

Управление членством в группах
```
# usermod -G group1,group2 user1

# usermod -a -G group1 user1

# usermod -a -G group2 user1

# gpasswd -a user1 group1
# gpasswd -a user1 group2
```
```
# gpasswd -d user1 group1
```
```
# cat /etc/group
# getent group
# id user1
```
Назначение пользователю shell
```
# cat /etc/shells
```
```
/usr/sbin/nologin
/usr/bin/passwd
```
```
# usermod -s /usr/bin/passwd user1
```

Управление временем жизни учетной записи и ее пароля
```
# man chage
```
```
# chage -l userX

# chage -E 2020-08-30 userX
```
Удаление учетной записи
```
# userdel -r student
```
