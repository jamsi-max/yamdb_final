# FROM python:3.7-slim
# RUN mkdir /app
# COPY api_yamdb/requirements.txt /app
# RUN pip install -r /app/requirements.txt --no-cache-dir
# COPY . /app
# WORKDIR /app/api_yamdb/
# CMD ["python3", "manage.py", "runserver", "0:8000"]
FROM python:3.7-slim

WORKDIR /app

COPY api_yamdb/requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY /api_yamdb .

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]

