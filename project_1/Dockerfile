FROM python:3.11-alpine

WORKDIR /app

RUN apk add --no-cache \
musl-dev \
gcc \
python3-dev

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

FROM python:3.11-alpine

WORKDIR /app

RUN apk add --no-cache 

COPY --from=0 /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages

COPY . /app/
RUN rm -rf /root/.cache /tmp/* 

RUN adduser -D myuser
USER myuser

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
