# taski-docker

## taski - сервис для отслеживания выполнения задач.

## Установка
Клонируйте репозиторий на свой компьютер:

'''
git clone https://github.com/D1qqo/taski-docker.git
cd taski_final
'''

Создайте файл .env и заполните его своими данными. Перечень данных указан в корневой директории проекта в файле .env.example.

## Создание Docker-образов
Замените username на ваш логин на DockerHub:

'''
cd backend
docker build -t d1qqo/taski_backend:latest .
cd frontend
docker build -t d1qqo/taski_frontend:latest .
cd gateway
docker build -t d1qqo/taski_gateway:latest .
'''

## Загрузите образы на DockerHub:

'''
docker push d1qqo/taski_backend:latest
docker push d1qqo/taski_frontend:latest
docker push d1qqo/taski_gateway:latest
'''
