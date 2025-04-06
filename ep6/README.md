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

   7.1 In "firstweb"  ```setting.py``` modify by adding app name in this case is ```myapp``` and ALLOWED_HOSTS:
   
   ``` Python
       # Application definition

       INSTALLED_APPS = [
          'django.contrib.admin',
          'django.contrib.auth',
          'django.contrib.contenttypes',
          'django.contrib.sessions',
          'django.contrib.messages',
          'django.contrib.staticfiles',
          'myapp',
       ]
   ```
   ``` Python
       ALLOWED_HOSTS = ['*']
   ```

   7.2 In "firstweb"  ```urls.py``` adding path of ```myapp```:

   ``` Python
       from django.contrib import admin
       from django.urls import path, include
      
       urlpatterns = [
           path('admin/', admin.site.urls),
           path('', include('myapp.urls')),
       ]  
   ```

   7.3 Create a file named ```urls.py``` in myapp folder:

   ``` Python
       from django.urls import path
       from .views import *

       urlpatterns = [
          path('', home) #receive "home" function from "views.py"
       ]
   ```

   7.4 Add function in ```views.py``` file for displaying in our host:

   ``` Python
       from django.shortcuts import render
       from django.http import HttpResponse

       # Create your views here.
       def home(request):
       return HttpResponse("<h1>Hello World!</h1>")
   ```
   7.5 In "firstweb"  ```settings.py``` Add Script:
   ``` Python
       STATIC_URL      = '/static/'
       STATIC_ROOT     = BASE_DIR / "static"  
       STATICFILES_DIR = [BASE_DIR / "static"]
       MEDIA_URL       = "/media/" 
       MEDIA_ROOT      = BASE_DIR / "media"
   ```
      | Setting           | Purpose                                                                         |
      |-------------------|---------------------------------------------------------------------------------|
      | `STATIC_URL`      | URL prefix for accessing static files (e.g., `/static/css/style.css`)           |
      | `STATIC_ROOT`     | The directory where static files are collected using `collectstatic` (usually for production) |
      | `STATICFILES_DIRS`| Extra directories Django will search for static files during development        |
      | `MEDIA_URL`       | URL prefix for serving user-uploaded files (like profile pics)                  |
      | `MEDIA_ROOT`      | The directory on disk where uploaded media files are stored                     |

   7.6 In "firstweb"  ```urls.py``` Add Script:
   ``` Python
       if settings.DEBUG:
       urlpatterns += static(settings.MEDIA_URL, document_root = settings.MEDIA_ROOT)
       urlpatterns += static(settings.STATIC_URL, document_root = settings.STATIC_ROOT)
   ```

   FULL SCRIPT:
   ``` Python
       from django.contrib import admin
       from django.urls import path, include
       from django.conf.urls.static import static
       from django.conf import settings

       urlpatterns = [
             path('admin/', admin.site.urls),
             path('', include('myapp.urls')),
       ]

       if settings.DEBUG:
             urlpatterns += static(settings.MEDIA_URL, document_root = settings.MEDIA_ROOT)
             urlpatterns += static(settings.STATIC_URL, document_root = settings.STATIC_ROOT)
   ```

      - ```static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)``` - Serves uploaded files (like user images)
      - ```static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)``` - Serves static files (CSS, JS, etc.)
   In production, static and media files are usually served by a web server like Nginx, not Django.


   





   
