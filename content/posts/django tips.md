---
title: Django Tips
date: "2020-08-19"
template: "post"
draft: false
slug: "django-tips"
category: "Programming"
tags:
  - "Python"
  - "django"
  - "Programming"
description: "Django tips and tricks"
socialImage: "/media/42-line-bible.jpg"
---

### **Token authentication**

We need to add [`signals.py`](http://signals.py/) in the app root folder. This will create the token on calling the login api. Post this, all the api will be intercepted and will be checked for the token in the request.

```python
from django.conf import settings
from django.dispatch import receiver
from rest_framework.authtoken.models import Token
from django.db.models.signals import post_save

@receiver(post_save, sender=settings.AUTH_USER_MODEL)
def create_auth_token(sender, instance=None, created=False, **kwargs):
    if created:
        Token.objects.create(user=instance)
```

In the the `[models.py](http://models.py)` import the following line

`from .signals import create_auth_token # noqa`

Then run migrate and migrations 

```bash
$ python manage.py makemigrations
$ python manage.py migrate # db migrate
```

### Create your custom djnago commands

Go to your base `app` folder. Create folder `management` and inside that create one more folder `commands`. `app/management/commands`

Now create a file called `seed_db.py.`

Presuming you have created models companies and users. You can change for your models.

```python
from django.conf import settings
from django.core.management import call_command
from django.core.management.base import BaseCommand
from project.users.models import  Company, User

user_admin = [
    {"name":"admin","password":"password"}
]
companies = ["Google","Apple"]
def create_superuser(username, password):
    print('Creating user {}:{}'.format(username, password))
    user, _ = User.objects.get_or_create(username=username)
    user.is_staff = True
    user.is_superuser = True
    user.save()
    user.set_password(password)
    user.save()
    return user

class Command(BaseCommand):

    def handle(self, *args, **options):

        call_command('makemigrations')
        call_command('migrate')

        if settings.DEBUG:
            print('Creating dummy user')

        print('Creating users and bots')
        for k in user_admin:
            create_superuser(k["name"],k["password"])

        print('Creating companies')
        for company in companies:
            Company.objects.get_or_create(name=company)
```

Now you can run

```bash
python manage.py seed_db # seed_db is the python file name inside the commands
```