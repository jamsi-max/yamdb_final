FROM python:3.7-slim

WORKDIR /app

COPY api_yamdb/requirements.txt .

RUN pip install --upgrade pip

RUN pip install -r requirements.txt --no-cache-dir

COPY api_yamdb/ .

# 
# RUN python manage.py migrate
# RUN python manage.py collectstatic
COPY api_yamdb/static/redoc.yaml ./static
# 

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]

