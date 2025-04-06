# virtualenv
### 🔍 What is virtualenv?
virtualenv is a tool that lets you create isolated Python environments. This means you can have separate sets of Python packages for different projects without conflicts.

1. Install virtualenv:
   ```bash
   pip install your-package-name
   ```

2. Create a virtual environment:
   ```bash
   python -m virtualenv venv
   ```

3. Activate the virtual environment:
   - On Windows:
      ```bash
      venv\Scripts\activate
      ```
   - On macOS/Linux:
     ```bash
      source venv/bin/activate
      ```
4. Deactivate it when you're done:
   ```bash
      deactivate
   ```

# Django
1. Install Django:
   ```bash
   pip install django
   ```
   
2. Create a new Django project named  ```firstweb ```:
   ```bash
   django-admin startproject firstweb
   ```
   Breaking it down:
   - ```django-admin```: A command-line utility provided by Django to perform various tasks like creating projects, apps, etc.
   - ```startproject```: A subcommand that tells Django to set up the basic structure for a new project.
   - ```firstweb```: The name of my new project.

3. Run the development server:
   ```bash
   cd firstweb
   python manage.py runserver
   ```
4. Visit to ```http://127.0.0.1:8000``` in my browser.
5. Apply database migrations:
   ```bash
   python manage.py migrate
   ```
6. Create an admin (superuser) account:
   ```bash
   python manage.py createsuperuser
   ```

   ```
   Username: admin
   Email address: admin@example.com
   Password: ********
   Password (again): ********
   Superuser created successfully.
    ```
   Once the superuser is created, run the development server:
   ```bash
   python manage.py runserver
   ```
7. Create a new Django app named ```<app name>```
   ```bash
   python manage.py startapp <app name>
   ```
   📂 What startapp creates:
   Running startapp myapp creates this structure:
   
   ```text
   myapp/
   ├── __init__.py
   ├── admin.py
   ├── apps.py
   ├── migrations/
   │   └── __init__.py
   ├── models.py
   ├── tests.py
   └── views.py
   ```
   
   Here's what some of those files do:
   - ``` models.py ```     – Define your database models here.
   - ``` views.py ```      – Handle the logic for your web pages.
   - ``` admin.py ```      – Customize how models appear in the admin panel.
   - ``` apps.py ```       – App config settings.
   - ``` migrations/ ```   – Stores migration files that apply model changes to the DB.


   





   
