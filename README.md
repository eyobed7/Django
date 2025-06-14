# Django
📌 What is Django?
Django is a Python-based web framework that helps you build web applications faster and with less code.
It handles common tasks like:

User authentication

Database operations

Page routing

Admin panel creation

Think of Django as a set of tools that helps you create websites without building everything from scratch.

🧪 Prerequisites
Make sure you have:

✅ Python installed (you can check by running python --version)
✅ Internet connection
✅ A code editor like Visual Studio Code

📁 Step-by-Step Setup
1. Create a Project Folder
Open Command Prompt and type:

```Terminal
cd Desktop
mkdir Django
cd Django
code .
```
This creates a folder called Django on your desktop and opens it in Visual Studio Code.

## 2. Create a Virtual Environment
A virtual environment isolates your project so you can install packages without affecting other projects.

```Terminal
python -m venv vdjango
```
To activate the virtual environment:

```Terminal
vdjango\Scripts\activate
```

Now you’ll see (vdjango) at the beginning of your terminal — this means it’s activated.

## 3. Install Django
Run:

```
pip install django
```
You’ll see Django and its dependencies being installed. You can check by typing:

```Terminal
pip list
```
You should see something like this:

```
Django 5.2.1
asgiref ...
sqlparse ...
tzdata ...
```

To verify the installation:

```Terminal
python -m django --version
````
---
## 4. Create Your Django Project
Let’s create a project named mysite:

```Terminal
django-admin startproject mysite
cd mysite
```
---
## 5. Run the Django Development Server
To start your first server:

```Terminal
python manage.py runserver
```
# Django Apps

In the Django web framework, a project and an app are related but distinct concepts. A Django project is a collection of settings and configurations for a particular Django web application. It acts as a container for one or more Django apps. It defines the database settings, installed apps, middleware, templates, and other project-level configurations.

On the other hand, an app in Django is a self-contained, reusable module that represents a specific functionality or feature of your web application. A Django project can have multiple apps, each responsible for a specific aspect of the application. Apps contain models (database schemas), views (handling HTTP requests and responses), templates (HTML files), and other app-specific files. Examples of apps might include a blog app, a user authentication app, an e-commerce app, etc.

---

## Creating Django Apps

You create a new app within a project using the following command:

```bash
python manage.py startapp book_store
```
When you create a new Django app using the above command, Django generates several files within the app directory.
```
book_store/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```
- *admin.py:* This file is used to register your models with the Django admin interface, which provides a user-friendly way to manage your application’s data through a web interface.

- *apps.py:* This file is used to define the configuration and metadata for your app. It contains a Config class that inherits from django.apps.AppConfig and includes metadata such as the app name and label.

- *migrations/:* This directory is created the first time you run migrations for your app. It stores migration files that keep track of changes to your models, allowing you to evolve your database schema over time.

- *models.py:* This file is where you define your data models, which represent the database tables for your application. Models are defined as Python classes that inherit from django.db.models.Model.

- *tests.py:* This file is used to write unit tests for your app’s models, views, and other components. Django provides a built-in testing framework to help you write and run tests.

- *views.py:* This file contains the view functions that handle HTTP requests and return HTTP responses. Views are responsible for processing user input, interacting with models, and rendering templates.
  
  **Setting Up Your Django App**
***Adding a Simple View***
Open the file book_store/views.py and add the following lines:

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Welcome to my book store.")
```
This is the simplest view possible in Django. To call the view, we need to map it to a URL — and for this we need a URLconf.

**Creating URLconf**
In the book_store directory, create a file called urls.py and add the following code:
```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.index, name="index"),
]
```
**Updating Root URLconf**
Open the project_name/urls.py and update it as follows:

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("books/", include("book_store.urls")),
    path("admin/", admin.site.urls),
]
```
**Registering the App**
The next step is to register the app so that it will be included when any tools are run. We do this by adding it to the INSTALLED_APPS list found in the settings.py file:

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'book_store.apps.BookStoreConfig',
]
```
**Migrating and Running the Django App**
Now we need to migrate our changes. To do this, run the following two commands one after the other:
```python
python manage.py makemigrations
python manage.py migrate
```
## 0. Introduction to Django Development Environment Setup

**Objective:** Gain familiarity with Django by setting up a Django development environment and creating a basic Django project. This task aims to introduce you to the workflow of Django projects, including project creation and running the development server.

**Task Description:**  
Install Django and create a new Django project named LibraryProject. This initial setup will serve as the foundation for developing Django applications. You’ll also explore the project’s default structure to understand the roles of various components.

**Steps:**  
**Install Django:**

- Ensure Python is installed on your system.  
- Install Django using pip: `pip install django`.

**Create Your Django Project:**

- Create a new Django project by running: `django-admin startproject LibraryProject`.

**Run the Development Server:**

- Navigate into your project directory (`cd LibraryProject`).  
- Create a `README.md` file inside the LibraryProject.  
- Start the development server using: `python manage.py runserver`.  
- Open a web browser and go to `http://127.0.0.1:8000/` to view the default Django welcome page.

**Explore the Project Structure:**  
Familiarize yourself with the created project structure. Pay particular attention to:

- `settings.py`: Configuration for the Django project.  
- `urls.py`: The URL declarations for the project; a “table of contents” of your Django-powered site.  
- `manage.py`: A command-line utility that lets you interact with this Django project.

**Repo:**  
GitHub repository: `Final_DjangoLearnLab`  
Directory: `Introduction_to_Django`


# Rendering HTML in Django

Rendering HTML in Django is a fundamental part of building a web application. Here's a quick step-by-step guide to help you render HTML using Django:

---

## ✅ 1. **Set Up Your Django Project (if not already)**

If you haven't started a project:

```bash
django-admin startproject myproject
cd myproject
python manage.py startapp myapp
```

---

## ✅ 2. **Create a View in Your App**

In `myapp/views.py`:

```python
from django.shortcuts import render

def home(request):
    return render(request, 'home.html')  # 'home.html' is your template
```

---

## ✅ 3. **Create a Template Folder and HTML File**

Inside your app folder (`myapp`), create a folder named `templates`, and inside it, create `home.html`:

```
myapp/
├── templates/
│   └── home.html
```

**Example `home.html`:**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Login Form</title>
</head>
<body>
    <h2>Login Page</h2>

    <!-- ✅ Success message display -->
    {% if message %}
        <p style="color: green;">{{ message }}</p>
    {% endif %}

    <form method="POST">
        {% csrf_token %}
        <label for="username">Username:</label><br>
        <input type="text" name="username" required><br><br>

        <label for="password">Password:</label><br>
        <input type="password" name="password" required><br><br>

        <button type="submit">Login</button>
    </form>
</body>
</html>

```

---

## ✅ 4. **Configure Template Settings**

In `settings.py`, make sure `TEMPLATES` is set up correctly (it usually is by default):

```python
'DIRS': [],  # Or you can add ['templates'] if using a global templates folder
```

Also, make sure `'APP_DIRS': True` is enabled.

---

## ✅ 5. **Map URL to the View**

In `myapp/urls.py` (create it if it doesn't exist):

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
```

Then include `myapp` URLs in your project's main `urls.py`:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```

---

## ✅ 6. **Run the Server**

```bash
python manage.py runserver
```

Open your browser at `http://127.0.0.1:8000/` — you should see your rendered HTML page.

---

# Django Login Form with MySQL Database

Great! You're building a Django login form that saves data (like username and password) to a MySQL database. Here's a complete step-by-step guide to achieve this:

---

## ✅ Overview

1. Connect Django to MySQL
2. Create a model (User or similar)
3. Create a form in HTML
4. Save form data to the database
5. Render the form and handle submissions

---

## 🔧 Step 1: Connect Django to MySQL

### 1. Install MySQL client:

```bash
pip install mysqlclient
```

If this fails on Windows, you can use:

```bash
pip install pymysql
```

Then in `__init__.py` of your project folder (next to `settings.py`):

```python
import pymysql
pymysql.install_as_MySQLdb()
```

---

### 2. Configure MySQL in `settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',  # or your database server
        'PORT': '3306',
    }
}
```

Make sure this DB exists in MySQL already or create it manually using a tool like phpMyAdmin or MySQL CLI.

---

## 🧱 Step 2: Create a Model

In `myapp/models.py`:

```python
from django.db import models

class User(models.Model):
    username = models.CharField(max_length=150)
    password = models.CharField(max_length=128)  # Store hashed passwords in real apps!

    def __str__(self):
        return self.username
```

---

## ⚙️ Step 3: Create and Apply Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

---

## 📝 Step 4: Create HTML Login Form

In `myapp/templates/login.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Login Form</title>
</head>
<body>
    <h2>Login Page</h2>
    <form method="POST">
        {% csrf_token %}
        <label for="username">Username:</label><br>
        <input type="text" name="username" required><br><br>

        <label for="password">Password:</label><br>
        <input type="password" name="password" required><br><br>

        <button type="submit">Login</button>
    </form>
</body>
</html>
```

---

## 🧠 Step 5: Create View Logic

In `myapp/views.py`:

```python
from django.shortcuts import render
from .models import User

def login_view(request):
    if request.method == 'POST':
        username = request.POST.get('username')
        password = request.POST.get('password')

        # Save to DB (not secure - just for learning)
        user = User(username=username, password=password)
        user.save()

        return render(request, 'login.html', {'message': 'User saved successfully!'})

    return render(request, 'login.html')
```

---

## 🌐 Step 6: Map URL to View

In `myapp/urls.py`:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('login/', views.login_view, name='login'),
]
```

In `project/urls.py`:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```

---

## ✅ Step 7: Run the Server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/login/` and try submitting the form. Data should be saved to your MySQL database.

---

### ⚠️ Important Notes

* **Don't store passwords in plain text** in production! Use Django's authentication system with hashing.
* Use `ModelForm` for better form management.
* You can enable user login using Django's `auth` system if desired.

---






