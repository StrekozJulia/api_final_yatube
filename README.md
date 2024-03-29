# Сервис API для взаимодействия с проектом Yatube
____
## Yatube - социальная сеть для блогеров

Полностью реализует доступ к функционалу социальной сети [Yatube](https://github.com/StrekozJulia/hw05_final.git) через API
____

## Технологии:
* Python 3.7
* Django 2.2.16
* Pillow 8.3.1
* Pytest 6.2.4
* Django 2.2.16
* DjangoRestFramework 3.12.4
* PyJWT==2.1.0
* Djoser==2.1.0

### Как запустить проект:

1. Клонировать репозиторий, выполнив следующую команду в консоли:
```
git clone https://github.com/StrekozJulia/api_final_yatube.git
```
2. Перейти в него в командной строке
```
cd api_final_yatube
```
3. Cоздать виртуальное окружение
```
py -3.7 -m venv venv
```
4. Активировать виртуальное окружение
```
source venv/scripts/activate
```
5. Обновить пакетный установщик
```
py -3.7 -m pip install --upgrade pip
```
6. Установить зависимости из файла requirements.txt
```
pip install -r requirements.txt
```
7. Выполнить миграции
```
python manage.py migrate
```
8. Запустить проект
```
python manage.py runserver
```
____
## Доступные запросы к API:

+ http://127.0.0.1.8000/api/v1/users/ - создание нового пользователя
    Тип запроса: POST
    Передаваемые данные: {"username": string, "password": string}

+ http://127.0.0.1.8000/api/v1/jwt/create/ - создание токена
    Тип запроса: POST
    Передаваемые данные: {"username": string, "password": string}

+ http://127.0.0.1.8000/api/v1/jwt/refresh/ - получение токена
    Тип запроса: POST
    Передаваемые данные: {"refresh": string}

+ http://127.0.0.1.8000/api/v1/jwt/verify/ - валидация токена
    Тип запроса: POST
    Передаваемые данные: {"token": string}

+ http://127.0.0.1.8000/api/v1/posts/ - доступ к списку публикаций
    Тип запроса: GET, POST
    Передаваемые данные (POST): {"text": string, 
                                "image": string or null,
                                "group": string or null}

+ http://127.0.0.1.8000/api/v1/posts/{id}/ - доступ к одиночной публикации по id
    Тип запроса: GET, PUT, PATCH, DELETE 
    Передаваемые данные (PUT, PATCH): {"text": string, 
                                      "image": string or null,
                                      "group": string or null}

+ http://127.0.0.1.8000/api/v1/posts/{post_id}/comments/ - доступ к списку комментариев к посту 
    Тип запроса: GET, POST
    Передаваемые данные (PUT, PATCH): {"text": string}

+ http://127.0.0.1.8000/api/v1/posts/{post_id}/comments/{id} - доступ к одиночному комментарию к посту по id
    Тип запроса: GET, PUT, PATCH, DELETE 
    Передаваемые данные (PUT, PATCH): {"text": string}

+ http://127.0.0.1.8000/api/v1/groups/ - доступ к списку сообществ
    Тип запроса: GET

+ http://127.0.0.1.8000/api/v1/posts/{id}/ - доступ к одиночному сообществу по id
    Тип запроса: GET

+ http://127.0.0.1.8000/api/v1/follow/ - доступ к подпискам пользователя
    Тип запроса: GET, PUT
    Передаваемые данные (PUT): {"following": string}

+ http://127.0.0.1.8000/api/v1/follow/?search=string - поиск автора среди подписок пользователя
    Тип запроса: GET
