## Steps
* Install Python (I'm using 3.6.0)
* Install Postgresql (I'm using 9.6)
* Install `virtualenv`
```sh
pip install virtualenv
```
* Activate `virtualenv`
* Install dependencies
```sh
pip install psycopg2
pip install django
pip install djangorestframework

# Using Knox for user login realted operations (Login, Logout) 
pip install django-rest-knox
```

* Create a Database
```sh
# for linux
sudo su postgres

# for windows
psql -U postgres

CREATE DATABASE test_django_postgres;

# Creating an user with " CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypass'"
CREATE USER <username> WITH ENCRYPTED PASSWORD '<password>';

# Permissions
ALTER ROLE rahulsarker SET client_encoding TO 'utf8';
ALTER ROLE rahulsarker SET default_transaction_isolation TO 'read committed';
ALTER ROLE rahulsarker SET timezone TO 'UTC';
GRANT ALL PRIVILEGES ON DATABASE test_django_postgres TO <username>;
```

* Configure projects `settings.py`
```sh
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'test_django_postgres',
        'USER': '<username>',
        'PASSWORD': '<password>',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```

* Migrate Database
```sh
python manage.py makemigrations
python manage.py migrate
```

* Create a Super User
```sh
python manage.py createsuperuser
```

* Run the project
```sh
python api/manage.py runserver
```
