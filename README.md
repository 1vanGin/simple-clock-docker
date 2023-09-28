# Шаги для разворачивания Frontend с Docker

1. npm init
2. index.js, html, css в папке static
3. Dockerfile
4. Сборка докер файла
```
sudo docker build -t simpleclockapp .
// -t simpleclockapp - задаёт имя для image
```
5. Запуск докера
```
sudo docker run -d simpleclockapp 
```
6. Описываем docker-compose
```
sudo docker compose up -d
```
7. Описываем nginx
```
sudo docker compose up -d nginx
```
8. Подключаем SSL (docker-compose, nginx/default.conf)
9. Подключаемся к серверу
```
ssh root@<ip>
```
10. Установить на сервер [docker](https://docs.docker.com/engine/install/ubuntu) и git
```
apt install git

установка докера по ссылке:
от install apt repository 
до параграфа install from a package
```
11. Загрузить проект в gitHub/gitLab
12. Склонировать проект на сервер
```
git clone <project-url>
```
13. Перейти в папку с проектом
```
cd simple-clock/
```
14. Запускаем nginx
```
docker compose up -d nginx
```
15. Вводим на сервере команду (для SSL)
```
docker compose run --rm --entrypoint "\
 certbot certonly --webroot -w /var/www/certbot \
 --email <some_email> 
 -d <url without "http://">
 --agree-tos
 --force-renewal" certbot
```
