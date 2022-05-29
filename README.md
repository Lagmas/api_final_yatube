***API для соцсети блогеров Yatube***

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

Выполнить миграции и запустить проект:

Windows
> python manage.py migrate

> python manage.py runserver

Linux
> python3 manage.py migrate

> python3 manage.py runserver


***Использованные технологии.***

Python 3.7, Django 2.2.16,  Django Rest Framework 3.12.4, Djoser, Simple JWT


*** Примеры запросов к API:***

```
GET /api/v1/posts/

Response:
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {}
   ]
}

POST /api/v1/posts/

Response:
{
 "text": "string",
 "image": "string",
 "group": 0
}

Request:
{
 "id": 0,
 "author": "string",
 "text": "string",
"pub_date": "2019-08-24T14:15:22Z",
 "image": "string",
 "group": 0
}

GET /api/v1/follow/

Response:
[
  {
    "user": "string",
    "following": "string"
  }
]

POST /api/v1/follow/

Request:
{
  "following": "string
}

Response:
{
  "user": "string",
  "following": "string"
}

