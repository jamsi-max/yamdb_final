
# ✨Yamdb final CI/CD✨
### **CI/CD полный цикл проекта Yamdb final**
##### Стек технологий: Python, Django REST Framework, Docker, Git Action, Telegram API

[![yamdb_final](https://github.com/jamsi-max/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/jamsi-max/yamdb_final/actions/workflows/yamdb_workflow.yml)
#
###### Проект доступен по адресу
1) http://51.250.111.30/api/v1/
2) http://51.250.111.30/admin
3) http://51.250.111.30/redoc/
#
###### В проекте реализовано

- контейнерезация Docker Compose;
- автоматическое тестирование после обновления репозитория git;
- автоматическое сборка и деплой Docker image;
- автоматический деплой проекта на веб сервер;
- уведомление через телеграм-бота об успешном выпонении всех стадий CI/CD

## **Запуск проекта**
##### 1. Клонировать репозиторий
#
```sh
git clone https://github.com/jamsi-max/yamdb_final.git
```
##### 2. Сооздать файл ".env" рядом с **"manage .py"** следующего содержания:
#
> DB_ENGINE=django.db.backends.postgresql
> DB_NAME=postgres
> POSTGRES_USER=postgres
> POSTGRES_PASSWORD=postgres
> DB_HOST=db
> DB_PORT=5432

##### 3. Cоздать и активировать виртуальное окружение:
#
```sh
python -m venv env
```
```sh
venv\Scripts\acrivate
```

##### 4. Обновить pip:
#
```sh
python -m pip install --upgrade pip
```
##### 5. Установить зависимости из файла requirements.txt:
#
```sh
pip install -r requirements.txt
```
##### 6. Перейти в директорию "yamdb_final\infra" где находиться файл **"docker-compose.yaml"** и выполнить команду для запуска проекта в контейнерах:
`Внимание! Docker уже должен быть установлен и запущен`
```sh
docker-compose up -d
```
##### 7. Выполнить миграции:
#
```sh
docker-compose exec web python manage.py migrate
```
##### 8. Заполнить базу тестовыми данными:
#
```sh
docker-compose exec web python manage.py loaddata fixtures.json
```
##### 9. Создать суперпользователя:
#
```sh
docker-compose exec web python manage.py createsuperuser
```
##### 10. При необходимости собрать статику если стили и картинки не отображаются:
#
```sh
docker-compose exec web python manage.py collectstatic --no-input
```

### Документация проекта по адресу http://localhost/redoc
#
### Перед остановкой проекта создать резервную копию базы:
#
```sh
docker-compose exec web python manage.py dumpdata > /app/api_yamdb/fixtures.json
```
##### Для остановки проекта используйте команду:
#
```sh
docker-compose down
```

## Лицензия

MIT

**Бесплатный софт**
##### Автор проекта: Макс
##### Связь с автором(телеграмм): https://t.me/jony2024 
##### © Copyright **[jamsi-max](https://github.com/jamsi-max)**
