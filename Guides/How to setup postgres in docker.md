### Setting up with Postgres in Docker
- Compose. `Dockerfile`  in the root folder of the project
```
FROM python:3
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
WORKDIR /<work dir>
COPY requirements.txt /<work dir>/
RUN pip install -r requirements.txt
COPY . /<work dir>/
```
- Compose `requirements.txt`  in the root folder

```
Django==2.2
psycopg2>=2.8
pillow==5.4.1
```
- Compose `docker-compose.yml` as following

```
version: "3.9"
   
services:
  db:
	image: postgres
	restart: always
	environment:
	  - POSTGRES_NAME=postgres
      - POSTGRES_USER=root
      - POSTGRES_PASSWORD=postgres
      - POSTGRES_HOST_AUTH_METHOD=trust
    volumes:
      - ./data/db:/var/lib/postgresql/data
	ports:
      - "5432:5432"
    healthcheck:
	  test: ["CMD", "pg_isready"]
      interval: 1s
      timeout: 3s
      retries: 30
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/<work dir>
    ports:
      - "8000:8000"
    environment:
      - POSTGRES_NAME=postgres
      - POSTGRES_USER=root
      - POSTGRES_PASSWORD=postgres
    depends_on:
      - db
	    - condition: service_healthy
```
- Run from root folder (if `django-admin startproject` doesn't work, use `python3 -m django`

```
sudo docker-compose run web django-admin startproject <project name> .

sudo docker-compose run web python3 -m django startproject <project name> .
```
- `ls -l`  to check whether the project has been created
- `sudo chown -R $USER .`  to change the root user responsible (user with no group).
- Modify `settings.py` in the work-dir to contain,

```
# settings.py
   
import os
   
[...]
   
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('POSTGRES_NAME'),
        'USER': os.environ.get('POSTGRES_USER'),
        'PASSWORD': os.environ.get('POSTGRES_PASSWORD'),
        'HOST': 'db',
        'PORT': 5432,
    }
}
```
- Run `docker-compose up` to build the image.
- To stop the network, `docker-compose down -v`


# Tags
#guide