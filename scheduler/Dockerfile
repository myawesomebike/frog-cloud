FROM python:3.8-buster AS builder

ENV CELERY_BROKER_URL redis://fc-redis:6379/0
ENV CELERY_RESULT_BACKEND redis://fc-redis:6379/0
ENV POSTGRES_USER fcuser
ENV POSTGRES_PASSWORD fcpassword
ENV POSTGRES_HOST fc-database
ENV POSTGRES_DB fcdb

RUN apt-get update \
    && apt-get install -y --no-install-recommends g++ gcc \
    && rm -rf /var/lib/apt/lists/* \
    && pip install cryptography

WORKDIR /src

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD ["flask", "run", "--host", "0.0.0.0" ]