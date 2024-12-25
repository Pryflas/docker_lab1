# Используем легковесный базовый образ Python
FROM python:3.11-alpine

# Устанавливаем рабочую директорию
WORKDIR /app

# Устанавливаем зависимости
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

RUN apk add --no-cache 

# Копируем все файлы приложения
COPY . /app/

RUN rm -rf /root/.cache

# Создаем непривилегированного пользователя
RUN adduser -D appuser
USER appuser

# Выполняем миграции и запускаем сервер
CMD ["sh", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
