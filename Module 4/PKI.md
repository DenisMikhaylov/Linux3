Использование PKI
Сценарий:

развертывание корпоративного CA (на lan)
в client-ах добавляем сертификат CA в корневые центры сертификации

Установка и запуск сервера Apache на lan
```
# apt install apache2
```
Удаление index.html
Проверка открытие сайта

Создание центра сертификации

Настройка атрибутов базы CA в конфигурации ssl
```
lan# nano /etc/ssl/openssl.cnf
```
```
...
[ CA_default ]
...
dir           = /root/CA

certificate   = /var/www/html/ca.crt

crl           = /var/www/html/ca.crl

private_key   = $dir/ca.key
...
```
Созданеи структуры PKI
```
cd
mkdir CA
mkdir CA/certs
mkdir CA/newcerts
mkdir CA/crl
touch CA/index.txt
echo "01" > CA/serial
echo "01" > CA/crlnumber
```
Создание зашифрованного приватного ключа
```
lan# openssl genrsa -des3 -out CA/ca.key 2048

Generating RSA key, 2048 bits
Enter PEM pass phrase:Pa$$w0rd
Verifying - Enter PEM pass phrase:Pa$$w0rd
```
Настройка атрибутов организации в конфигурации ssl
```
lan# nano /etc/ssl/openssl.cnf
```
```
...
[ req_distinguished_name ]
...
countryName_default           = RU
stateOrProvinceName_default   = Moscow region
localityName_default          = Moscow
0.organizationName_default    = cko
organizationalUnitName_default = noc
emailAddress_default          = noc@corpX.un

[ req_attributes ]
...
```
``
