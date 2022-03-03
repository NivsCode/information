- Modify the `views.py`
```
from django.views.generic import ListView from .models import Book class BookListView(ListView): model = Book template_name = 'book_list.html'

```
- Modify project/urls.py
```
from django.contrib import admin from django.urls import path, include

urlpatterns = [ path('admin/', admin.site.urls), path('', include('books.urls')), # new ]

```
- Modify app/urls.py (create one if not present)
```
from django.urls import path from .views import BookListView

app_name = 'books'

urlpatterns = [ path('', BookListView.as_view(), name='home'), ]
```
- Create a template `app_name/templates/model_name_<action>.html` with `touch books/templates/books/book_list.html`
- Modify the html file
```
<!-- books/templates/books/book_list.html --> 
<h1>All books</h1> 
	{% for book in object_list %} 
	<ul> 
		<li>Title: {{ book.title }}</li>
		<li>Subtitle: {{ book.subtitle }}</li>
		<li>Author: {{ book.author }}</li>
		<li>ISBN: {{ book.isbn }}</li>
	</ul>
	{% endfor %}
```
