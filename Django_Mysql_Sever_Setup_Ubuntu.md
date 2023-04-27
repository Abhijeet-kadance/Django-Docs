## MYSQL SERVER SETUP WITH DJANGO (UBUNTU)

> For the Prerequisite for this we can create a basic Django Project and a app.

**Ubuntu Server MYSQL Setup**

---

> Log in to the Server : (--For this we are using a Ubuntu VM--):

    user@home:$>  pwd

You can check presend working directory, wherer are you right now on your linux machine.

---

**Update apt-get**

    user@home:$> sudo apt-get update

---

**Installing Mysql server and dev libraries**

    user@home:$> sudo apt-get install mariadb-server libmariadbclient-dev

---

**Install mysqlclient (PYPI) in virtual ewnviornment**

    user@home:$> cd /home/project-directory/

    Once inside Project Directory Create a virtual env (If Not already created )

    user@home:$> source /venv/bin/activate

    (venv)user@home:$> 

    Now you are inside your virtual enviornment. Install mysql-client

    (venv)user@home:$> pip install mysql-client

    ***NOTE***
    If Using Python3 you can use pip3 to install
    **********

---

**Create a database in Mysql**

Log into Mysql

    user@home:$> sudo mysql

        Once Inside we have to create a user so that we can start creating databases.

        MariaDB [(none)]> CREATE USER 'user'@'localhost' IDENTIFIED BY 'mypassword';

        Here we have created user with the HOST : Localhost and assigned a password to hi,

        MariaDB [(none)]> GRANT ALL PRIVILEGES ON * . * TO 'user'@'localhost' WITH GRANT OPTION;

        This will grant all the permissions on all the databases to user@localhost

        MariaDB[(none)]> FLUSH PRIVILEGES

        MariaDB[(none)]> CREATE DATABASE project_db;

        MariaDB[(none)]> exit

---
**Configuring Mysql setting in Django**

Go to settings.py file in your Django project directory 

There find the database settingsas 'DATABASES'

There would be a sqlite database configuration by default which we have to replace with the mysql settings so remove the Sqlite settings

and add this new settings

    DATABASES = {
        'default': {
            'ENGINE':'django.db.backends.mysql',
            'NAME':'project_db',
            'USER':'user',
            'PASSWORD':'mypassword',
            'HOST':'localhost',
            'PORT:'3306',
        }
    }

    Save It.
---

**Creating Django Model**

Inside Models file create a model name SearchEngine

    from django.db import models

    class SearchEngine(models.Model):
        url = models.CharField(max_lenght=255)
        isphp = models.BooleanField(default=False)
        search_time = models.DateTimeField(auto_now=True)

    ***NOTE***
    Keep in mind that you have registerd your app in settings.py file
    **********

    Now create the migrations 

    (venv)user@home:$> python manage.py makemigrations

    (venv)user@home:$> python manage.py migrate

    This way you can check your mysql database there would be a table named SearchRngine created into the project_db database.

    