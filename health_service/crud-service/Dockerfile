FROM --platform=linux/amd64 python:3.13-slim

WORKDIR /app

# Установим зависимости
RUN pip install --no-cache-dir fastapi uvicorn sqlalchemy

# Копируем код
COPY . /app

EXPOSE 8000

# Запуск приложения
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
