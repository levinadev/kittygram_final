# Kittygram

![CI/CD](https://github.com/levinadev/kittygram_final/actions/workflows/main.yml/badge.svg)

Kittygram — это приложение для обмена фотографиями кошек.

## Демо
- [Развернутый проект](https://kittygram.levinadev.ru/)  
- [Административная панель](https://kittygram.levinadev.ru/admin/)

## Возможности
- Загружать карточку с информацией о кошке — фото, имя, год рождения, цвет кота и достижения
- Редактировать информацию о кошке
- Удалять карточку с кошкой

## Установка и запуск локально

1. Клонировать репозиторий:
```
git clone https://github.com/levinadev/kittygram_final.git
cd kittygram_final
```

2. Создать файл `.env` в корне проекта на основе шаблона:
```
cp .env.example .env
```
При необходимости измените значения переменных в `.env` (например, `DJANGO_SECRET_KEY` и `DJANGO_ALLOWED_HOSTS`) под ваше окружение.

3. Запуск:
```
docker-compose -f docker-compose.production.yml up -d
```

4. После этого проект будет доступен по адресу: http://127.0.0.1:9000/

5. Остановка контейнеров:

```
docker-compose -f docker-compose.production.yml down
```

## Примеры запросов к API

1. Регистрация

```
curl -X POST http://127.0.0.1:8000/api/token/ \
  -H "Content-Type: application/json" \
  -d '{"username": "your_username", "password": "your_password"}'
```

Ответ:

```
{
    "email": "",
    "username": "your_username",
    "id": 4
}
```

2. Получить токен

```
curl -X POST http://127.0.0.1:8000/api/token/login/ \
  -H "Content-Type: application/json" \
  -d '{"username": "your_username", "password": "your_password"}'
```

Ответ:

```
{
  "auth_token": "your_token"
}
```

3. Получить список кошек

```
curl -X GET http://127.0.0.1:8000/api/cats/ \
  -H "Authorization: Token your_token"
```

4. Создать кошку

```
curl -X POST http://127.0.0.1:8000/api/cats/ \
  -H "Authorization: Token your_token" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Барсик",
    "color": "#000000",
    "birth_year": 2020,
    "achievements": [{"achievement_name": "Лучший охотник"}],
    "image": null
  }'
```

5. Обновить кошку

```
curl -X PATCH http://127.0.0.1:8000/api/cats/2/ \
  -H "Authorization: Token your_token" \
  -H "Content-Type: application/json" \
  -d '{"name": "Рыжик"}'
```

6. Удалить кошку

```
curl -X DELETE http://127.0.0.1:8000/api/cats/2/ \
  -H "Authorization: Token your_token"
```

## Технологии
- Python 3.11
- Django 3.2
- Django REST Framework
- PostgreSQL 13
- Docker & Docker Compose
- GitHub Actions (CI/CD)
- React (Frontend)
- Gunicorn
- Nginx

## Автор

- Имя: Анна
- Email: anna45dd@yandex.ru
- GitHub: https://github.com/levinadev
