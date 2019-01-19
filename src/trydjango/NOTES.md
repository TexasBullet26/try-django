# Notes

---

[Python Django Web Framework Video](https://www.freecodecamp.org/news/python-django-course/)

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

We are going to create a new app

Jump into the root of your project (where manage.py is located) (trydjango/src) and run:

`python manage.py startapp products`
`python manage.py startapp blog`
`python manage.py startapp profiles`
`python manage.py startapp cart`

(`python manage.py startapp [name_of_app]`)

- Each one of these _apps_ should do only one thing and do that one thing very well
  - For example, the products app should do just product related things, not cart related things
- The idea here is that each _app_ should be narrow in scope and focused. Once it starts to get wide in scope, that's when you start to bring it into another app

**How to use an app in the way of storing data** (36:45)

The _apps_ are really good for storing data and mapping what data you want to store to your database.

_(40:00 into video)_

Open up `trydjango/src/products/models.py`

We want to store a product (we want our backend to have memory of a product that we created). We can do this by adding the following to models.py:

```python
class Product(models.Model):
    title       = models.TextField()
    description = models.TextField()
    price       = models.TextField()
    summary     = models.TextField(default='this is cool!')
```

We also need to add this app to `settings.py` in `INSTALLED_APPS`:

```python
INSTALLED_APPS = [
    ...,
    ...,
    ...,
    ...,
    ...,
    ...,

    # third party

    # own
    'products',
]
```

From the terminal we can now run:

`python manage.py makemigrations`

and then:

`python manage.py migrate`

:flag: **Every time we make a change to any models.py we need to save and run `python manage.py makemigrations` and `python manage.py migrate`**

_(40:52 into video)_

So now we have this model and now we want to look at this model inside of the admin. So we go into `trydjango/src/products/admin.py` and add:

```python
from .models import Product
```

This is what we call a **relative import**. It's importing the Product class from the models.py file in the same products directory / module.

Then we add the following below to what we just added:

```python
admin.site.register(Product)
```

Save that and now we can add a new product from the admin page and it is saved in the database.

This is really the core and the basics of it all.

- A basic model saved in the database
- We can use this over and over again to save all kinds of data in the database
- THIS IS NOT A GREAT MODEL (Limited in scope on how it is)

## Create Product Objects in the Python Shell (42:34)
