1. If it's a project that handles backend and frontend separately. The folder structure should be something similar to this.
```
todo 
| ├──frontend 
  |  ├──React... 
| ├──backend
  |  ├──Django...

```

2. Create a django project within the backend project
```
# within the backend folder, run the following cmds
python -m django startproject config .

# To start the app,
python manage.py startapp <name>

# You need to check the sql or postgres before running this cmd
python manage.py migrate
```

3. Modify the settings.py to contain the `app` 
4. Create your models
5. Register your models in the admin site
6. Create a superuser
7. Modify to settings.py to contain [rest_framework settings](https://www.django-rest-framework.org/api-guide/settings/) and corsheaders
```
INSTALLED_APPS = [ 'django.contrib.admin', 'django.contrib.auth', 'django.contrib.contenttypes', 'django.contrib.sessions', 'django.contrib.messages', 'django.contrib.staticfiles', 
# 3rd party 
'rest_framework',
'corsheaders',
'todos', 
] 

# ---- DEV ONLY or PROJECT LEVEL PERMISSIONS----
REST_FRAMEWORK = { 
	'DEFAULT_PERMISSION_CLASSES': [
	  'rest_framework.permissions.AllowAny', 
] }
# ---- DEV ONLY or PROJECT LEVEL PERMISSIONS ----

MIDDLEWARE = [
'django.middleware.security.SecurityMiddleware',
'django.contrib.sessions.middleware.SessionMiddleware',
'corsheaders.middleware.CorsMiddleware',
'django.middleware.common.CommonMiddleware',
'django.middleware.csrf.CsrfViewMiddleware',
'django.contrib.auth.middleware.AuthenticationMiddleware',
'django.contrib.messages.middleware.MessageMiddleware',
'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

CORS_ORIGIN_WHITELIST = (
	'http://localhost:8000',
	'http://localhost:3000',
)

```

8. Add auth to config/urls.py (root)
```
from django.contrib import admin

from django.urls import include, path

urlpatterns = [ 
	path('admin/', admin.site.urls), 
	path('api/v1/', include('posts.urls')), 
	path('api-auth/', include('rest_framework.urls')), # new ]
```