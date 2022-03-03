1. Create `<app>/permissions.py`
2. Modify permissions.py to suit customized auth (which is usually just overriding `has_object_permission` within class)
```
form rest_framework import permissions

class Is AuthOrReadOnly(permissions.BasePermission):
	def has_object_permission(self, request, view, obj):
		if request.method in permissions.SAFE_METHODS:
		return True

	return obj.author == request.user
```
3. For reference, the [actual code on github](https://github.com/encode/django-rest-framework/blob/master/rest_framework/permissions.py)