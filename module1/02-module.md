2.1 Обновление систем

DPKG

# less /var/lib/dpkg/status

Установленные пакеты

# dpkg -l 

Содержимое пакета

# dpkg -L 

В какой пакет входит файл

# dpkg -S /etc/init.d/ssh

Удаление пакета
# dpkg -r firewalld

Использование менеджера пакетов APT

Настройка репозитория

# cat /etc/apt/sources.list

Проверить и добавить текст

#deb http://deb.debian.org/debian/ buster main contrib non-free
#deb http://deb.debian.org/debian buster-updates main contrib non-free

deb http://ftp.ru.debian.org/debian/ buster main contrib non-free
deb http://ftp.ru.debian.org/debian/ buster-updates main contrib non-free

deb http://security.debian.org/ buster/updates main contrib non-free

#deb-src http://deb.debian.org/debian buster main contrib non-free
#deb-src http://deb.debian.org/debian buster-updates main contrib non-free
#deb-src http://security.debian.org/ buster/updates main contrib non-free


Обновление списка доступных пакетов

# apt update

Поиск пакета

$ apt search antivirus

Информация о найденном пакете

$ apt show clamav-daemon

Какие пакеты зависят от пакета

$ apt depends ssh
