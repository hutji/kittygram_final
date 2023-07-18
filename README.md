#  Проект Kittygram
Здесь пользователи обмениваются фотографиями своих котиков, заводят новых друзей.

## Инструкция по запуску проекта из образов с Docker hub

Для запуска необходимо на создать папку проекта, например `kittygram_final` и перейти в нее:

```bash
mkdir kittygram_final
cd kittygram_final
```

В папку проекта скачиваем файл `docker-compose.production.yml` и запускаем его:

```bash
sudo docker compose -f docker-compose.production.yml up
```

Произойдет скачивание образов, создание и включение контейнеров, создание томов и сети.

## Запуск проекта из исходников GitHub

Клонируем себе репозиторий: 

```bash 
git clone git@github.com:hutji/kittygram_final.git
```

Выполняем запуск:

```bash
sudo docker compose -f docker-compose.yml up
```

## После запуска: Миграции, сбор статистики

После запуска необходимо выполнить сбор статистики и миграции бэкенда. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py migrate

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py collectstatic

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend cp -r /app/collected_static/. /backend_static/static/
```

И далее проект доступен на: 

```
http://localhost:9000/
```

## Остановка оркестра контейнеров

В окне, где был запуск **Ctrl+С** или в другом окне:

```bash
sudo docker compose -f docker-compose.yml down
```


## Технологии проекта

* #### Django REST Framework
* #### Python 3.9
* #### Gunicorn
* #### JS
* #### Node.JS
* #### Nginx
* #### PostgreSQL
* #### Docker

## Информация об авторе

- Лашков Павел Александрович, начинающий backend разработчик, г. Москва
- https://github.com/hutji

## Демо-версия сайта
- https://hutjikitty.zapto.org