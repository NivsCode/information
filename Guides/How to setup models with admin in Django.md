- Create the model in models.py under the app

```
from django.db import models

class ModelName(models.Model):
	attr1 = models.CharField()

	def __str__(self):
		return f''
```
- Run `python manage.py makemigrations` and `python manage.py migrate`
- Create superuser with `python manage.py createsuperuser`
- Alter admin.py to include books at [Link](http://127.0.0.1:8000/admin)
```
from django.contrib import admin
from .models import Book

admin.site.register(Book)
```