## Database Migration from Sqlite to Postgres

---

**Migrate from SQLite to PostgreSQL on developer Enviornment**

Steps to Perform :
---
-   Dump Exisiting Database into JSON object
-   Import database in PostgreSQL


---
**Dump Data from Existing Database Server**

TO do this you must be inside your django project and virtual enviornment:

    (venv)user@home >$ python manage.py dumpdata > datadump.json

You will Find a new File Datadump.json inside your Django Project Folder.

---
**Setup Your PostregSQL**

There are Few steps to setup a Postgres Server in your System (Windows|Linux|MAC-OS)

You cand find Online how to setup POSTGRESSQL in your System.

Follow This Link to setup Postgressql in Windows :

https://www.sqlshack.com/how-to-install-postgresql-on-windows/

---

**Configuiring Database settings in Django**

In your Django Project you can go to the settings.py file and check the default Database Setting


    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }

Changing the default SQLITE settings to POSTGRESQL Settings

    DATABASES = {
        'default': {
            'ENGINE':'django.db.backends.postgresql_psycopg2',
            'NAME': 'test_db',              # Postgres Database Name
            'USER': 'postgres',
            'PASSWORD': 'manager',
            'HOST': '127.0.0.1',            # Can be localhost or server IP
            'PORT': '5432',                 # Default PORT
        }
    }

---

**Installing the requied Libraries**

Install the postgresql library in your virtual environrment

    (venv)user@home >$ pip install psycopg2

---

**Syncing Model to Database**

We can sync Models to database once we have added new database configuration

    (venv)user@home >$ python manage.py migrate --run-syncdb


---

**Importing the datadump.json in Postgresql Database**

You can migrate the dump data to new database by using the following command

    (venv)user@home >$ python manage.py loaddata datadump.json



---

This Way You can use the New Postgresql Database with exisiting Database !!!