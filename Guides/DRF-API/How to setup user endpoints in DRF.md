1. Add new serializer for model
```
class UserSerializer(serializers.ModelSerializer): # new

class Meta:  
model = get_user_model() fields = ('id', 'username',)
```
3. New views for endpoint
```
from django.contrib.auth import get_user_model
from .serializers import UserSerializer
from rest_framwork import viewsets

class UserViewSet(viewsets.ModelViewSet): # new 
	queryset = get_user_model().objects.all() 
	serializer_class = UserSerializer
```
5. new URL routes for each endpoint
```
from django.urls import path
from rest_framework.routers import SimpleRouter
from .views import UserViewSet

router = SimpleRouter()
router.register('users', UserViewSet, basename='users')

```