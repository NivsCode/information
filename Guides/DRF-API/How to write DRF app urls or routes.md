1. Using simple router from rest_framework
```
from django.urls import path
from rest_framework.routers import SimpleRouter
from .views import UserViewSet, PostViewSet

router = SimpleRouter()
router.register('users', UserViewSet, basename='users')
router.register('', PostViewSet, basename='posts')

urlpatterns = router.urls
```

2. Custom views 
```
# Root urls.py

from django.contrib import admin from django.urls import include, path 

urlpatterns = [ 
	path('admin/', admin.site.urls), 
	path('api/',include('todos.urls')),
]
```

```
# app/urls.py

from django.urls import path 
from .views import TodoList, TodoDetail

urlpatterns = [ 
		path('<int:pk>/', TodoDetail.as_view()),
		path('', TodoList.as_view()), 
]
```
