FROM python:3.11

WORKDIR /app

# 1) Ставим системные питон-пакеты для рантайма образа (вне кода проекта)
RUN pip install --no-cache-dir --upgrade pip \
 && pip install --no-cache-dir gunicorn==23.0.0

# 2) Устанавливаем зависимости приложения
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 3) Копируем код
COPY . .

# 4) Запускаем через gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]
