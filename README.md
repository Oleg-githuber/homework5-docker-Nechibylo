# Домашняя работа "Контейнеризация"
Запустил контейнер в режиме демона с именем some-mysql с паролем для root "password" из mysql:8.0.31:
```sh
docker run -d --name some-mysql -e MYSQL_ROOT_PASSWORD=password mysql:8.0.31
```
![run some-mysql](/ScreenShots/1_mysql.png)
Запустил контейнер в режиме демона с именем myphp, связанный с контейнером some-mysql с именем хоста some-mysql, с пробросом порта 80 через порт 8081:
```sh
docker run -d --name myphp --link some-mysql:some-mysql -p 8081:80 -e PMA_HOST=some-mysql phpmyadmin/phpmyadmin
```
![run myphp](/ScreenShots/2_myphp.png)
Подключился к серверу через браузер по адресу localhost:8081:
![brouser](/ScreenShots/3_pw.png)
Ввел пароль password для пользователя root:
![brouser](/ScreenShots/4_web.png)
Удалил созданные контейнеры:
![remove](/ScreenShots/5_rm.png)
Повторил операцию с помощью yml-файла.
Создал файл docker-compose.yml:
![nano docker-compose.yml](/ScreenShots/6_yml.png)
Указал в файле параметры, которые ранее вводились в терминале:
![docker-compose.yml](/ScreenShots/7_nano.png)
Запустил docker-compose в режиме демона, с помощью предзаписаного yml-файла:
![docker compose](/ScreenShots/8_up.png)
Подключился к серверу через браузер по адресу localhost:8081 и ввёл пароль password:
![web brouser](/ScreenShots/9_web.png)
Удалил созданные контейнеры:
![remove](/ScreenShots/10_rm.png)

Работу выполнил Олег Нечибыло