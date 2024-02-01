# taski-docker

## taski - сервис для отслеживания выполнения задач.

## Стек используемых технологий:

Python, Django, Django Rest Framework, Docker, Gunicorn, NGINX

## Установка
Клонируйте репозиторий на свой компьютер:

```
git clone https://github.com/D1qqo/taski-docker.git
cd taski_final
```

Создайте файл .env и заполните его своими данными. Перечень данных указан в корневой директории проекта в файле .env.example.

## Создание Docker-образов
Замените username на ваш логин на DockerHub:

```
cd backend
docker build -t d1qqo/taski_backend:latest .
cd frontend
docker build -t d1qqo/taski_frontend:latest .
cd gateway
docker build -t d1qqo/taski_gateway:latest .
```

## Загрузите образы на DockerHub:

```
docker push d1qqo/taski_backend:latest
docker push d1qqo/taski_frontend:latest
docker push d1qqo/taski_gateway:latest
```

## Деплой на сервере

1Подключитесь к удаленному серверу

Создайте на сервере директорию taski через терминал

```
mkdir taski
```

Установка docker compose на сервер:

```
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin
```

В директорию taski/ скопируйте файлы docker-compose.production.yml и .env:

```scp -i path_to_SSH/SSH_name docker-compose.production.yml username@server_ip:/home/username/taski/docker-compose.production.yml
* ath_to_SSH — путь к файлу с SSH-ключом;
* SSH_name — имя файла с SSH-ключом (без расширения);
* username — ваше имя пользователя на сервере;
* server_ip — IP вашего сервера.
```

## Файл .env

DB_HOST=db DB_PORT=5432

POSTGRES_USER — имя пользователя БД (необязательная переменная, значение по умолчанию — postgres);
POSTGRES_PASSWORD — пароль пользователя БД (обязательная переменная для создания БД в контейнере);
POSTGRES_DB — название базы данных (необязательная переменная, по умолчанию совпадает с POSTGRES_USER). Таким образом, можно передать в окружение только переменную POSTGRES_PASSWORD — и будет создана БД с названием postgres и пользователем postgres.
