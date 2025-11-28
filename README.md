 URL Shortener Service на FastAPI

  Описание проекта
URL Shortener Service — это высокопроизводительный микросервис для сокращения ссылок, разработанный на современном фреймворке FastAPI. Проект демонстрирует возможности создания быстрых и масштабируемых веб-API.

 #
 
 Задачи проекта:
- Создать REST API для сокращения длинных URL
- Реализовать редирект с коротких ссылок на оригинальные
- Внедрить систему статистики переходов
- Обеспечить валидацию URL и генерацию уникальных кодов
- Создать автоматическую документацию API
#
  Архитектура проекта
 ```bush
url_shortener/              # Корневая директория проекта
├── app/                    # Пакет приложения
│   ├── __init__.py        # Инициализация пакета
│   ├── main.py           # Точка входа, эндпоинты API
│   ├── database.py       # Конфигурация БД, сессии
│   ├── models.py         # Модели SQLAlchemy (сущности БД)
│   ├── schemas.py        # Pydantic схемы (DTO)
│   ├── crud.py           # Бизнес-логика, операции с БД
│   └── utils.py          # Вспомогательные функции
├── requirements.txt       # Зависимо
сти проекта
└── .env                  # Конфигурация окружения
```
#
Основные эндпоинты
- `POST /shorten` - Создание короткой ссылки
- `GET /{short_code}` - Редирект на оригинальный URL
- `GET /stats/{short_code}` - Статистика переходов
- `GET /docs` - Автоматическая документация
#
  Установка и запуск

 Предварительные требования
- Python 3.8+
- FastAPI
- Uvicorn
- SQLite (или другая БД)

 Инструкция по запуску:


Установите зависимости:
```bush
pip install fastapi uvicorn sqlalchemy
```
Запустите приложение:
```bush
uvicorn app.main:app --reload
```
#
Приложение: http://localhost:8000

Документация: http://localhost:8000/docs

Альтернативная документация: http://localhost:8000/redoc
#
Функциональность
Создание короткой ссылки
Запрос:

```bush
POST /shorten
{
    "url": "[https://example.com/very/long/url/path](https://www.meme-arsenal.com/create/template/487159)"
}
Ответ:

json
{
    "short_code": "GYwh1p",
    "short_url": "[http://localhost:8000/a1b2c3](http://localhost:8000/GYwh1p)",
    "original_url": "[https://example.com/very/long/url/path](https://www.meme-arsenal.com/create/template/487159)"
}
```
#
Статистика переходов
Запрос:

```bush
GET /stats/a1b2c3
Ответ:

json
{
    "short_code": "GYwh1p",
    "original_url": "[https://example.com/very/long/url/path](https://www.meme-arsenal.com/create/template/487159)",
    "clicks": 15,
    "created_at": "2024-01-15T10:30:00"
}
```
#
 Технические особенности
Используемые технологии:
FastAPI - современный фреймворк для API

Pydantic - валидация данных и сериализация

SQLAlchemy - работа с базой данных

Uvicorn - ASGI сервер для запуска
#
Ключевые преимущества:
 Высокая производительность благодаря асинхронности
 Автоматическая документация Swagger/ReDoc
 Валидация URL на корректность
 Статистика переходов в реальном времени
 Уникальные коды для каждой ссылки
#
 Тестирование
Методология тестирования:
 Функциональное тестирование всех эндпоинтов
 Тестирование редиректов
 Проверка статистики
 Тестирование производительности
#
Пример теста:
```bush
python

def test_create_short_url():
    response = client.post("/shorten", json={"url": "https://example.com"})
    assert response.status_code == 200
    assert "short_code" in response.json()
```
#
 Результаты проекта
Достигнутые цели:
Создан работающий сервис сокращения ссылок
Реализована полная цепочка: создание → редирект → статистика
Обеспечена валидация и обработка ошибок
#
Примеры использования:
Создание короткой ссылки
Переход по короткой ссылке (редирект на оригинал)
Просмотр статистики по количеству переходов

 Авторы и участники
[Кристиан] - разработчик, тестирование, документация
GitHub: [ссылка на ваш GitHub](https://github.com/kiberboss112/FastApi/edit/main/README.md)
Email: [yakoff.kristian@yandedx.ru]
