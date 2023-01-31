# API для Yatube


## Описание
Социальная сеть для публикации постов. Здесь можно публиковать посты, комментировать их, осуществлять подписку на авторов.
Проект реализован на [Django REST framework](https://www.django-rest-framework.org/).


## Как запустить проект:

1. Kлонируем репозиторий:
```
git clone 
```
2. Cоздаем виртуальную среду:
```
python3 -m venv venv
```
3. Активируем виртуальную среду:
```
source venv/bin/activate
```
4. Устанавливаем зависимости:
```
pip install -r requirements.txt
```
5. Запустите dev-сервер:

```
python manage.py runserver
```

## Документация к API:

http://127.0.0.1:8000/redoc/

## Примеры запросов

- ### Получение постов

Request: ```GET http://127.0.0.1:8000/api/v1/posts/?limit=1&offset=1```

Response:
```
{
    "count": 3,
    "next": "http://127.0.0.1:8000/api/v1/posts/?limit=1&offset=2",
    "previous": "http://127.0.0.1:8000/api/v1/posts/?limit=1",
    "results": [
        {
            "id": 2,
            "author": "root",
            "text": "post2 post2 post2 post2 post2 post2 post2",
            "pub_date": "2023-01-30T20:00:38.841490Z",
            "image": null,
            "group": 2
        }
    ]
}
```
- ### Создание поста

Request: ```POST http://127.0.0.1:8000/api/v1/posts/?limit=1&offset=1```
```
{
"text": "string",
"group": 1
}
```

Response:
```
{
    "id": 4,
    "author": "root",
    "text": "string",
    "pub_date": "2023-01-31T12:55:44.364543Z",
    "image": null,
    "group": 1
}
```
- ### Получение поста
Request: ```GET http://127.0.0.1:8000/api/v1/posts/1/```

Response:
```
{
    "id": 1,
    "author": "root",
    "text": "post1 post1 post1 post1",
    "pub_date": "2023-01-30T20:00:23.792749Z",
    "image": null,
    "group": 1
}
```
- ### Получение групп
Request: ```GET http://127.0.0.1:8000/api/v1/groups/```

Response:
```
[
    {
        "id": 1,
        "title": "group1",
        "slug": "group1",
        "description": "group1group1group1group1group1group1"
    },
    {
        "id": 2,
        "title": "group2",
        "slug": "group2",
        "description": "group2"
    }
]
```
- ### Получение группы
Request: ```GET http://127.0.0.1:8000/api/v1/groups/1/```

Response:
```
{
    "id": 1,
    "title": "group1",
    "slug": "group1",
    "description": "group1group1group1group1group1group1"
}
```



- ### Добавление комментария
Request: ```POST http://127.0.0.1:8000/api/v1/posts/1/comments/```
```
{
"text": "comment"
}
```
Response:
```
{
    "id": 1,
    "author": "root",
    "post": 1,
    "text": "comment",
    "created": "2023-01-31T13:07:43.297253Z"
}
```

## Автор
- [Александр Матияка](https://github.com/alexsevv)