FROM ubuntu:20.04

ENV PYTHONUNBUFFERED 1
ARG DEBIAN_FRONTEND=noninteractive

WORKDIR /app/backend

COPY requirements.txt /app/backend/

RUN apt-get update && apt-get -y install gnupg2 wget git python3-pip build-essential libncursesw5-dev libssl-dev \
libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev
RUN apt-get -y install python3-dev
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
# RUN apt-get -y install postgresql-13 postgresql-client-13
# RUN apt-get -y install postgis postgresql-13-postgis-3
RUN apt-get update && apt-get install -y postgresql-12 postgresql-client-12
RUN apt-get install -y postgis postgresql-12-postgis-3 postgresql-12-postgis-3-scripts

COPY . /app/backend/

CMD [ "python3", "manage.py", "runserver", "0.0.0.0:8000" ]
