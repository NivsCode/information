a. [Viewsets](https://www.django-rest-framework.org/api-guide/viewsets/): Modify `views.py` to reflect changes (Instead of writing list and detail as separate classes, we can combine with viewsets)

```
from django.contrib.auth import get_user_model
from rest_framework import viewsets
from .models import Post
from .permissions import IsAuthorOrReadOnly
from .serializers import PostSerializer, UserSerializer

class PostViewSet(viewsets.ModelViewSet):
	permission_classes = (IsAuthorOrReadOnly,)
	queryset = Post.objects.all()
	serializer_class = PostSerializer

class UserViewSet(viewsets.ModelViewSet):
	queryset = get_user_model().objects.all()
	serializer_class = UserSerializer
```

b. With **class level permissions**
```
# todos/views.py
from rest_framework import generics, permissions
from .models import Todo
from .serializers import TodoSerializer

# generics.ListCreateAPIView
class TodoList(generics.ListAPIView):
	permission_classes = (permissions.IsAuthenticated,)
	queryset = Todo.objects.all()
	serializer_class = TodoSerializer

# generics.RetrieveUpdateDestroyAPIView
class TodoDetail(generics.RetrieveAPIView):
	permission_classes = (permissions.IsAuthenticated,)
	queryset = Todo.objects.all()
	serializer_class = TodoSerializer

```

c. Create class based views in views.py
1. Create classes `<Object>List(APIView)` to handle index and bulk creation.
2. Create class `<Object>Detail(APIView)` to handle retrieval, update, delete an instance.
3. Specify the permissions the class will have from [link](https://www.django-rest-framework.org/api-guide/permissions/)
```
class ClientList(APIView):
"""
List all snippets or create a new Client.
"""

	permission_classes = [permissions.IsAuthenticated]

	def get(self, request, format=None):
		clients = request.user.client_set.all()
		serializer = ClientSerializer(clients, many=True)
		return Response(serializer.data)
		
	def post(self, request, format=None):
		serializer = ClientSerializer(data=request.data)
		if serializer.is_valid():
			serializer.save()	
			return Response(serializer.data, status=status.HTTP_201_CREATED)
		return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)


class ClientDetail(APIView):
"""
Retrieve, Update or delete a Client instance.
"""
	permission_classes = [permissions.IsAuthenticated]
	
	def get_object(self, pk):
		try:
			return Client.objects.get(pk=pk)
		except Client.DoesNotExist:
			raise Http404
	
	def get(self, request, pk, format=None):	
		client = self.get_object(pk)
		serializer = ClientSerializer(client)
		return Response(serializer.data)
	
	def put(self, request, pk, format=None):
		client = self.get_object(pk)
		serializer = UpdateClientSerializer(client, request.data)
		if serializer.is_valid():
			serializer.save()
			return Response(serializer.data)
		return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)

	def delete(self, request, pk, format=None):
		client = self.get_object(pk)
		client.delete()
		return Response(status=status.HTTP_204_NO_CONTENT)
```
