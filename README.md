<<<<<<< HEAD
# Домашнее задание к занятию «Система мониторинга Zabbix» Королев Е.В.

Задание 1

Установите Zabbix Server с веб-интерфейсом.
Процесс выполнения

    1 Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
    2 Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
    3 Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
    4 Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.

Требования к результаты

   1 Прикрепите в файл README.md скриншот авторизации в админке.
   2 Приложите в файл README.md текст использованных команд в GitHub.


Ответ:

1 ![1](https://github.com/Evgenii199130/-zabbix-.-.-/blob/main/Scrin/1.png)

2 
  

1 su

2 apt update

3 apt install postgresql

4 wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb

5 dpkg -i zabbix-release_6.0-4+debian11_all.deb

6 apt update 

7  # apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts

8  systemctl status zabbix server-service

9 su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'

10 su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'

11 zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbi

12 find / -name zabbix_server.conf

13 nano /etc/zabbix/zabbix_server.conf

14 sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf

15 cat /etc/zabbix/zabbix_server.conf |grep DBPassword

16 systemctl restart zabbix-server apache2

17 systemctl enable zabbix-server apache2

18 systemctl status zabbix server-service

=======
# zabbix
>>>>>>> 7eb82873cc9a348d40b00e90968512586b4481ca
Задание 2

Установите Zabbix Agent на два хоста.
Процесс выполнения

   1  Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
   2 Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
   3 Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
   4 Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
   5 Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.

Требования к результаты

    1 Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
    2 Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
    3 Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
    4 Приложите в файл README.md текст использованных команд в GitHub


Ответ:

1 ![1](https://github.com/Evgenii199130/-zabbix-.-.-/blob/main/Scrin/2.1.png)

 ![2](https://github.com/Evgenii199130/-zabbix-.-.-/blob/main/Scrin/2.2.jpg)

 ![3](https://github.com/Evgenii199130/-zabbix-.-.-/blob/main/Scrin/2.3.png)

2
# wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
# sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb
# apt update
# apt install zabbix-agent
# systemctl restart zabbix-agent
# systemctl enable zabbix-agent  
