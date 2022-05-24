# CRUD для Yatube

Реализация API для всех моделей приложения posts.

API доступен только аутентифицированным пользователям. Используется аутентификацию по токену TokenAuthentication. Аутентифицированный пользователь авторизован на изменение и удаление своего контента; в остальных случаях доступ предоставляется только для чтения. При попытке изменить чужие данные возвращается код ответа 403 Forbidden.

### Для взаимодействия с ресурсами настроены эндпоинты:
+ api/v1/api-token-auth/ (POST): передаём логин и пароль, получаем токен
+ api/v1/posts/ (GET, POST): получаем список всех постов или создаём новый пост
+ api/v1/posts/{post_id}/ (GET, PUT, PATCH, DELETE): получаем, редактируем или удаляем пост по id
+ api/v1/groups/ (GET): получаем список всех групп
+ api/v1/groups/{group_id}/ (GET): получаем информацию о группе по id
+ api/v1/posts/{post_id}/comments/ (GET, POST): получаем список всех комментариев поста с id=post_id или создаём новый, указав id поста, который хотим прокомментировать
+ api/v1/posts/{post_id}/comments/{comment_id}/ (GET, PUT, PATCH, DELETE): получаем, редактируем или удаляем комментарий по id у поста с id=post_id

## Как запустить проект
Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/kh199/api_yatube
```

Cоздать и активировать виртуальное окружение:
```
python3 -m venv env
source env/bin/activate
```

Установить зависимости из файла requirements.txt:
```
python3 -m pip install --upgrade pip
pip install -r requirements.txt
```

Выполнить миграции:
```
python3 manage.py migrate
```

Запустить проект:
```
python3 manage.py runserver
```