Стек
Python (FastAPI или Flask, в зависимости от того, что выбрано в коде)

Docker

Kubernetes (Deployment, Service, Ingress)

Структура
health_service/ – исходный код сервиса

health_service/k8s/ – манифесты для Kubernetes (deployment, service, ingress, configmap и т.д.)

Запуск локально (без Docker)
Установить зависимости (при необходимости создать виртуальное окружение):

bash
pip install -r requirements.txt
Запустить приложение (команда может отличаться, нужно смотреть в main.py):

bash
python main.py
После старта API обычно доступно на http://localhost:8000 или http://localhost:5000.

Сборка и запуск через Docker
Собрать образ:

bash
docker build -t health-service:local .
Запустить контейнер:

bash
docker run -d -p 8000:8000 --name health-service health-service:local
Проверить работу сервиса по адресу http://localhost:8000.

Деплой в Kubernetes
Предполагается, что кластер уже настроен и kubectl подключён.

Применить ConfigMap (если есть):

bash
kubectl apply -f k8s/configmap.yaml
Применить Deployment и Service:

bash
kubectl apply -f k8s/crud-deployment.yaml
Применить Ingress (если используется):

bash
kubectl apply -f k8s/ingress.yaml
Проверить, что поды запустились:

bash
kubectl get pods
kubectl get svc
kubectl get ingress
Примеры запросов
Создание записи: POST /patients

Получение списка: GET /patients

Получение по id: GET /patients/{id}

Обновление: PUT /patients/{id}

Удаление: DELETE /patients/{id}

