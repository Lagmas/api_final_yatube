**API для соцсети блогеров Yatube**

* У неаутентифицированных пользователей доступ к API только на уровне чтения.
* Исключение — эндпоинт /follow/: доступ к нему только аутентифицированным пользователям.
* Аутентифицированным пользователям разрешено изменение и удаление своего контента; в остальных случаях доступ предоставляется только для чтения.

***Установка.***

Клонировать репозиторий и перейти в него:

> git clone ...

Cоздать и активировать виртуальное окружение:

Windows
> python -m venv venv

> source venv/Scripts/activate

Linux
> python3 -m venv venv

> source venv/bin/activate

Установить зависимости из файла requirements.txt:

Windows
> python -m pip install --upgrade pip

> pip install -r requirements.txt

Linux
> python -m pip install --upgrade pip

> pip install -r requirements.txt

Сгенерировать и вставить в файл settings.py SECRET_KEY:

> python manage.py shell

|>>>from django.core.management.utils import get_random_secret_key

|>>>get_random_secret_key()

YOUR_KEY

|>>> quit()

скопировать полученное значение в settings.py SECRET_KEY = 'YOUR_KEY'

Выполнить миграции и запустить проект:

Windows
> python manage.py migrate

> python manage.py runserver

Linux
> python3 manage.py migrate

> python3 manage.py runserver

***Примеры.***
```
GET http://127.0.0.1:8000/api/v1/posts/
[
    {
        "id": 1,
        "author": "User3",
        "text": "В лесу родилась ёлочка, в лесу она росла...",
        "pub_date": "2022-02-23T16:39:25.754620Z",
        "image": null,
        "group": 1
    },
...

...
POST http://127.0.0.1:8000/api/v1/posts/
{
"text": "string",
"image": "string",
"group": 0
}
Response samples 201
{
"id": 0,
"author": "string",
"text": "string",
"pub_date": "2019-08-24T14:15:22Z",
"image": "string",
"group": 0
}
```
```
PATCH http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
{
"text": "string"
}
Response samples 200
{
"id": 0,
"author": "string",
"text": "string",
"created": "2019-08-24T14:15:22Z",
"post": 0
}
```

***Использованные технологии.***

Python 3.7, Django 2.2.16,  Django Rest Framework 3.12.4, Djoser, Simple JWT


```
Алексей
```
