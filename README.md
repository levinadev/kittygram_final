# Kittygram

Проект Kittygram — это приложение для обмена фотографиями кошек.

Оно позволяет:
- Загружать карточку с информацией о кошке — фото, имя, год рождения, цвет кота и достижения
- Редактировать информацию о кошке
- Удалять карточку с кошкой
---

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

---

## Установка и запуск

1. Клонирование репозитория:

```
git clone https://github.com/levinadev/kittygram_final.git
```


3. Запуск контейнеров:

```
docker-compose -f docker-compose.production.yml up -d
```

4. Остановка контейнеров:
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

Автор

- Имя: Анна
- Email: anna45dd@yandex.ru
- GitHub: https://github.com/levinadev
