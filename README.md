# Домашнее задание к занятию «Кластеризация и балансировка нагрузки»

### Задание 1
- Запустите два simple python сервера на своей виртуальной машине на разных портах
- Установите и настройте HAProxy, воспользуйтесь материалами к лекции.
- Настройте балансировку Round-robin на 4 уровне.
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy.

------

### Выполнения задания 1

 Запустил сразу три сервера на виртуальной машине на разных портах и проверил работоспособность.

 ![image](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/3%20servera.png)

 ![image](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/3%20servera%20test.png)

Установил HAProxy c конфигурацией и проверил статус
 
![image](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/haproxy%20status.png)

Конфигурация haproxy для балансировки по методу Round-robin на 4 уровне.

```
listen web_tcp
        bind :1325
        server s1 127.0.01:8888 check inter 3s
        server s2 127.0.01:9999 check inter 3s
        server s3 127.0.01:8500 check inter 3s

```
[Файл haproxy.cfg](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/01_haproxy.cfg)

HAProxy Statistics

![image](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/Stats%20tcp.png)


### Задание 2
- Запустите три simple python сервера на своей виртуальной машине на разных портах
- Настройте балансировку Weighted Round Robin на 7 уровне, чтобы первый сервер имел вес 2, второй - 3, а третий - 4
- HAproxy должен балансировать только тот http-трафик, который адресован домену example.local
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy c использованием домена example.local и без него.

------

### Выполнения задания 2

запустил три сервера : Server1 порт: 8888, Server2 порт: 9999,Server3 порт: 8500

![image](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/3%20сервера%202.png)

[Файл haproxy2.cfg](https://github.com/Byzgaev-I/Cluster_and_balansing/blob/main/02_haproxy.cfg)
