FROM python:3.8-slim

ENV PYTHONUNBUFFERED 1

COPY ./requirements.txt requirements.txt
COPY ./src /app
COPY entrypoint.sh /entrypoint.sh

RUN apt-get update && apt-get install -qq -y \
    build-essential libpq-dev netcat --no-install-recommends

RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /app

RUN adduser --disabled-password --gecos '' user

USER user

ENTRYPOINT ["sh", "/entrypoint.sh"]