### Models
- Do not follow fat models, Instead split into business logic and data access (Querysets + model manager)
	- dataset queries are handled by Django querysets
	- the managers and the querysets are contained in `managers.py` 
	```
	from Django.DB import models

	Class ProductQuerySet(models.query.QuerySet):
		
	```


### DRF
- [Add names to urls]() (eg: For rootpath, it's `home`)
- Create a dedicated `api` app to contain all API-specific files for the entire project. 

- Always version your APIs-v1, v2, etc when you make a large change, there may be some lage time before various consumers of the api can also update
```
# config/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [ 
	path('admin/', admin.site.urls),
	path('api/v1/', include('posts.urls')),]
```

- The implicit default settings are designed for the devs' convenience to jump and start working in a local dev environment. These default settings are not appropriate for production though
- With token authentication, the tokens stored in both cookies and localstorage are vulnerable to XSS attacks. The best practice is to store tokens in a cookie with `httpOnly` and `Secure` cookie flags.

### Migrations
- Always run `python manage.py makemigrations/migrate <app_name>` to run migrations or the app alone. This is easier to debug.
# Tags
#bestpractices