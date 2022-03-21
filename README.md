## Принт 15. Проект: запуск docker-compose


# Запуск проекта:

Клонировать репозиторий
```bash
git clone https://github.com/ivan-chekunkov/infra_sp2
```
Cоздать и активировать виртуальное окружение:
```bash
python3 -m venv env
source env/bin/activate
python3 -m pip install --upgrade pip
```
Установить зависимости из файла requirements.txt:
```bash
pip install -r api_yamdb/requirements.txt
```
Запуск контейнеров с приложением:
```bash
cd infra/
```
Создать файл .env и заполнить по шаблону ниже
```bash
docker-compose up -d --build
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
Остановить приложение:
```bash
docker-compose down -v
```


# Описание файла .env

```python
SECRET_KEY=<...> # ключ из settings.py
DB_ENGINE=<...> # указываем, что работаем с postgresql
DB_NAME=<...> # имя базы данных
POSTGRES_USER=<...> # логин для подключения к базе данных
POSTGRES_PASSWORD=<...> # пароль для подключения к БД (установите свой)
DB_HOST=<...> # название сервиса (контейнера)
DB_PORT=<...> # порт для подключения к БД
```
