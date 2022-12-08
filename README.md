# Сервис уведомлений

## Установка и запуск

1. Склонировать репозиторий с Github:

````
git clone https://github.com/IvanPonomarev64/mailing_service.git
````
2. Перейти в директорию проекта

3. Создать виртуальное окружение:

````
python -m venv venv
````

4. Активировать окружение: 

````
source\venv\bin\activate
````
5. В файле .evn заполнить необходимые данные: ```TOKEN = '<your token>'```
 
6. Установка зависимостей:

```
pip install -r requirements.txt
```

7. Создать и применить миграции в базу данных:
```
python manage.py makemigrations
python manage.py migrate
```
8. Запустить сервер
```
python manage.py runserver
```
9. Запустить celery
```
celery -A notification_service worker -l info
```
10. Запустить flower

```
celery -A notification_service flower --port=5555
```
***
### Запуск тестов
``` 
python manage.py test
```
***
## Запуск проекта с помощью docker-compose


1. Склонировать репозиторий с Github
```
git clone https://github.com/IvanPonomarev64/mailing_service.git
```
2. Перейти в директорию проекта
3. В файле .evn заполнить необходимые данные: ```TOKEN = '<your token>'```
4. Запустить контейнеры 
``` 
docker-compose up -d
 ```
5. Остановка работы контейнеров 
```
docker-compose stop
```
***
```http://0.0.0.0:8000/api/``` - api проекта

```http://0.0.0.0:8000/api/clients/``` - клиенты

```http://0.0.0.0:8000/api/mailings/``` - рассылки

```http://0.0.0.0:8000/api/mailings/fullinfo/``` - общая статистика по всем рассылкам

```http://0.0.0.0:8000/api/mailings/<pk>/info/``` - детальная статистика по конкретной рассылке

```http://0.0.0.0:8000/api/messages/``` - сообщения

```http://0.0.0.0:8000/docs/``` - docs проекта

```http://0.0.0.0:5555``` - celery flower

***
