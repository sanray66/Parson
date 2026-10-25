<div align="center">

# 🧠 Parson

**AI-анализ психотипа по 10 вопросам**

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?logo=sqlalchemy&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)


</div>



## О проекте

**Parson** — полноценное full-stack веб-приложение, которое превращает короткий опрос в персональный разбор личности.

1. Пользователь отвечает на **10 вопросов**.
2. Нажимает кнопку **«Анализ»**.
3. Бэкенд отправляет ответы в LLM через **OpenRouter API**.
4. Пользователь получает **развёрнутый психологический портрет** и **разбор каждого своего ответа**: что он означает и о чём говорит.

> ⚠️ Parson — развлекательно-исследовательский проект. Результат генерируется нейросетью и не является клинической диагностикой или заменой консультации специалиста.

## 🧰 Технологии

| Слой | Технологии |
|---|---|
| Frontend | Next.js, TypeScript |
| Backend | Python, FastAPI, Pydantic, asyncio |
| База данных | PostgreSQL 16, SQLAlchemy (async ORM), Alembic (миграции) |
| AI | OpenRouter API |
| Инфраструктура | Docker, Docker Compose, nginx |

## 🏗 Архитектура

![Архитектура](docs/architecture.png)

Фронтенд общается с бэкендом по **REST API**: создаёт пользователя, отправляет его ответы на вопросы и запрашивает готовый анализ. Весь трафик проходит через **nginx**, который выступает единой точкой входа.

## 🚀 Быстрый старт

Нужны только **Docker** и **Docker Compose**.

```bash
# 1. Клонируем репозиторий
git clone https://github.com/sanray66/Parson.git
cd parson

# 2. Создаём файл с переменными окружения
cp .env.example .env
# и подставляем свой ключ OpenRouter

# 3. Запускаем всё одной командой
docker compose up --build
```

После запуска приложение доступно по адресу **http://localhost:8080**

### ⚙️ Переменные окружения

Пример `.env`:

```env
DATABASE_URL=postgresql+asyncpg://postgres:password@postgres:5432/parson
OPENROUTER_API_KEY=your_openrouter_api_key
DB_USER=postgres
DB_PASSWORD=password
DB_NAME=parson
```

| Переменная | Описание |
|---|---|
| `DATABASE_URL` | Строка подключения бэкенда к PostgreSQL (asyncpg) |
| `OPENROUTER_API_KEY` | Ключ API OpenRouter ([получить](https://openrouter.ai/keys)) |
| `DB_USER` / `DB_PASSWORD` / `DB_NAME` | Данные для инициализации контейнера PostgreSQL |

## 🔌 API

Интерактивная документация (Swagger) доступна на `/docs`.

### Пользователи

| Метод | Путь | Описание |
|---|---|---|
| `GET` | `/users/` | Список пользователей |
| `POST` | `/users/` | Создать пользователя |
| `GET` | `/users/{user_id}/` | Получить пользователя по ID |

### Ответы пользователей

| Метод | Путь | Описание |
|---|---|---|
| `GET` | `/user_message/{user_id}/` | Получить ответы пользователя на вопросы |

### Анализ

| Метод | Путь | Описание |
|---|---|---|
| `POST` | `/analysis/` | Отправить ответы и получить AI-анализ психотипа |
| `GET` | `/analysis/{user_id}/` | Получить сохранённый анализ пользователя |

---

<div align="center">

⭐ Если проект понравился — поставь звезду!

</div>
