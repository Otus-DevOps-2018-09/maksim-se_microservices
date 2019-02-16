FROM python:3.6.0-alpine

WORKDIR /app
COPY . /app
# установка зависимостей
RUN apk --update add --virtual build-dependencies python-dev build-base \
  && pip install --upgrade pip \
  && pip install -r /app/requirements.txt \
  && apk del build-dependencies

ENV POST_DATABASE_HOST post_db
ENV POST_DATABASE posts
# запуск сервиса
ENTRYPOINT ["python3", "post_app.py"]

