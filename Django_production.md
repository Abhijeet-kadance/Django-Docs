# Production server ENV settings #

> We mostly prefer create .env file in the main Profile Folder where you find the manage.py file

> You can add some importing settings and credentials in .env file 

    - Set Debug settings = to 0|1 (On|Off) (For Production server we prefer to keep DEBUG=0 for ignoring development Error Pages)

    - Django Admin Credentials that include 
        * SuperUser Username
        * SuperUser Password
        * SuperUser Email
    
    - (DataBase)
        * Postgres SQL Settings
        * MySql Settings
        * MongoDB Settings
        * SQLite Settings
            This includes 
                - DB Name
                - DB Password
                - DB User
                - DB Host
                - DB Port
    
    - Other Server Settings
        - Redis Server
        - Elasctic Search
        - Rabbit MQ Server
        and so on .....

        This includes mostly
            - Port No
            - Host name
    
    - Most Importantly 
        .env file have SECRET KEY that we have to hide in Production server

    
    - Also Mail server Setting


- For .env to work we have to install "django-dotenv" library in our environment.

        pip install django-dotenv

- Do a 

        pip freeze

and add that to requrements.txt file

---

***Setting Up dot-env file***

---

> Locate andgo to wsgi.py file

> import pathlib

> Add
    
    CURRENT_DIR = pathlib.Path(__file__).resolve().parent
    BASE_DIR = CURRENT_DIR.parent

    OR --

    BASE_DIR = Path(__file__).resolve().parent.parent

    both will work fine !!

> Add ENV FILE PATH

        ENV_FILE_PATH = BASE_DIR/ ".env"
    
> Add the dotenv configuration

        dotenv.read_dotenv(str(ENV_FILE_PATH)

---

***Setting manage.py***

---

> Go to manage.py file and

    import dotenv

    inside the condition : 
    
    if __name__ == '__main__':
        dotenv.read_dotenv()
        main()
    