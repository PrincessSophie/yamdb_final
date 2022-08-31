# yamdb_final
![example workflow](https://github.com/PythonGun/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


## О себе
Привет! Меня зовут София, я учусь на программиста и проххожу курсы в Яндекс Практикуме.

## Инструкции по запуску (через GitHub)
## 1.Склонировать репозиторий через консоль:
`https://github.com/PrincessSophie/infra_sp2.git` 
## 2. Создать .env файл внутри директории infra (на одном уровне с docker-compose.yaml) Пример .env файла:
- `SECRET_KEY = 'p&l%385148kslhtyn^##a1)ilz@4zqj=rq&agdol^##zgl9(vs'` 
- `DB_ENGINE=django.db.backends.postgresql`
- `DB_NAME=postgres`
- `POSTGRES_USER=postgres`
- `POSTGRES_PASSWORD=123`
- `DB_HOST=db`
- `DB_PORT=5432`

## 3. Запуск тестов (опционально, если не нужно - переходите к следующему шагу) Создать и активировать виртуальное пространство, установить зависимости.
Для Windows:
- `cd infra_sp2` 
- `python -m venv venv`
- `source venv/Scripts/activate`
- `cd api_yamdb`
- `pip install -r requirements.txt`
- `cd ..`
- `pytest` 

Для Mac/Linux:
- `cd infra_sp2`
- `python3 -m venv venv`
- `source venv/bin/activate`
- `cd api_yamdb`
- `pip install -r requirements.txt`
- `cd ..`
- `pytest`

## 4.Запуск Docker контейнеров: Убедиться, что Docker установлен и готов к работе
- `docker --version`

Запустите docker-compose

- `cd infra/`
- `docker-compose up -d`

## 5.Выполните миграции, создайте суперпользователя и перенесите статику:

- `docker-compose exec web python manage.py migrate/`
- `docker-compose exec web python manage.py createsuperuser`
- `docker-compose exec web python manage.py collectstatic --no-input`

## 6.Наполните базу данных тестовыми данными:

- `docker-compose exec web python manage.py dbfill`

## 7.Проверьте доступность сервиса

- `http://localhost/admin`

