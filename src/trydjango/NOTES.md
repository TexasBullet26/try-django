# Notes

---

## Create a Virtual Environment (virtualenv)

---

Run the following in the directory that you want your virtual environment in:

`virtualenv -p python3 .`

Run the following to activate your virtual environment:

`source bin/activate`

## Install Django

`pip install django==2.0.7`

## Create Project

---

Create `src` directory and run:

`django-admin startproject trydjango .`

Run the following to run server:

`python manage.py runserver`

## Settings

---

`src/trydjango/settings.py`

### Hooking up Django and the Database together

From the terminal run:

```python
python manage.py migrate
```

## Built-In Components

---

1. Run: `python manage.py migrate` and make sure there's no errors

2. Create user: `python manage.py createsuperuser`

- This will allow us to create a user that can access the admin

- Follow directions in terminal (create username and password)

## Your First App Component (33:57)

---
