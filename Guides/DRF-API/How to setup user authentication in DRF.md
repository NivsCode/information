1. Modify `DEFAULT_AUTHENTICATION_CLASSES`  in `REST_FRAMEWORK` in `settings.py`
```
REST_FRAMEWORK = { 'DEFAULT_PERMISSION_CLASSES': [ 'rest_framework.permissions.IsAuthenticated', ], 'DEFAULT_AUTHENTICATION_CLASSES': [ # new 'rest_framework.authentication.SessionAuthentication', 'rest_framework.authentication.TokenAuthentication' ], }
```
Sessions are used to power the browsable API and the ability to log in and log out. Basic authentication is used to pass the session ID in the HTTP headers for the API itself.

2. Modify `INSTALLED_APPS` in settings.py
```
INSTALLED_APPS = [ 'django.contrib.admin', 'django.contrib.auth', 'django.contrib.contenttypes', 'django.contrib.sessions', 'django.contrib.messages', 'django.contrib.staticfiles', 


'rest_framework', 
'rest_framework.authtoken', <----
'posts', 
]
```
4. `rest_framework.authtoken` requires db migrations. Run `python manage.py migrate`.
5. Implement user authentication with [django-allauth](https://github.com/pennersr/django-allauth) and [dj-rest-auth](https://github.com/iMerica/dj-rest-auth)
	1. Make sure that `dj-rest-auth==1.1.0`  and `django-allauth~=0.42.0` is installed
	2. Modify `settings.py` ([Note for SITE_ID](https://docs.djangoproject.com/en/3.1/ref/contrib/sites/))
	```
		INSTALLED_APPS = [ 'django.contrib.admin', 
		'django.contrib.auth', 'django.contrib.contenttypes', 'django.contrib.sessions', 'django.contrib.messages', 'django.contrib.staticfiles',
		'django.contrib.sites', <----
	'rest_framework', 'rest_framework.authtoken',
	'allauth', <-----
	'allauth.account', <-----
	'allauth.socialaccount', <-----
	'dj_rest_auth', <-----
	'dj_rest_auth.registration', <-----
	'posts', ]

	EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend' <-----
	SITE_ID = 1 <-----
	```
	3. Modify `urls.py`
	```
	from django.contrib import admin
	from django.urls import include, path

	urlpatterns = [
		path('admin/', admin.site.urls),
		path('api/v1/', include('posts.urls'))
		path('api-auth', include('rest_framework.urls')),
		path('api/v1/dj-rest-auth', include('dj_rest_auth.urls')), <---
		path('api/v1/dj-rest-auth/registration', include('dj_rest_auth.registration.urls')), <----
	]
	```
	4. The endpoints are available at `http://127.0.0.1:8000/api/v1/dj-rest-auth/registration/`, `http://127.0.0.1:8000/api/v1/dj-rest-auth/login/` and `http://127.0.0.1:8000/api/v1/dj-rest-auth/logout/` and `http://127.0.0.1:8000/api/v1/dj-rest-auth/password/reset` and `http://127.0.0.1:8000/api/v1/dj-rest-auth/password/reset/confirm`.