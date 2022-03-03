# Schema generation
1. Install packages
```
pipenv install pyyaml==5.3.1
pipenv install uritemplate==3.0.1
```
3. Decide on static file schema or dynamic option
	- For the static file option, run from cmdline
	`python manage.py generateschema > openapi-schema.yml`
    - For the dynamic option, update root `urls.py` with `get_schema_view()`. The schema will served at `http://127.0.0.1:8000/openapi`
	```
	from django.contrib import admin
	from django.urls import include, path
	from rest_framework.schemas import get_schema_view

	urlpatterns = [
		path('openapi', get_schema_view(
			title='Blog API',
			description='A sample API for learning DRF',
			version='1.0.0'
		), name='openapi-schema'),
	]
	```

# Documentation generation
1. Install packages
`pipenv install drf-yasg==1.17.1`
3. Add to installed_apps config in `settings.py`
```
INSTALLED_APPS = [
...
'drf_yasg',
]
```
5. Modify `urls.py` to serve the openAPI endpoint at `http://127.0.0.1:8000/swagger/`.

```
from django.contrib import admin
from django.urls import include, path
from rest_framework import permissions
from drf_yasg.views import get_schema_view
from drf_yasg import openapi

schema_view = get_Schema_view(
	openapi.Info(
		title='Blog API',
		default_version='v1',
		description='A sample API for learning DRF',
		terms_of_service='https://www.google.com/policies/terms/',
		contact=openapi.Contact(email='hello@example.com'),
		license=openapi.License(name='BSD License')
	),
	public=True,
	permission_classes=(permissions.AllowAny,),
)

urlpatterns = [
	path('swagger/', schema_view.with_ui(
		'swagger', cache_timeout=0), name='schema-swagger-ui'),
	path('redoc/', schema_view.with_ui(
	'redoc', cache_timeout=0), name='schema-redoc'),
]
```

# References
1. [DRF Documentation](https://www.django-rest-framework.org/topics/documenting-your-api/)
2. [drf-yasg documentation](https://drf-yasg.readthedocs.io/en/stable/)
4. [Swagger](https://swagger.io/tools/swagger-ui/)
5. [ReDoc](https://github.com/Redocly/redoc)
6. [OpenAPI](https://www.openapis.org)
 