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
