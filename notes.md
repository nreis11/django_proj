For models to show up in the admin page, you must register them in the admin.py of the app

```
admin.site.register(Post)
```

Crispy forms are great for styling and formatting.

### Auth

In templates, Django has acccess to "user" object. You do not need to pass it in as context.

```
{% if user.is_authenticated %}
```

### Media

Adding media has different methods depending if prod or dev env:

```
if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

### Signal

It's like a dispatch once a condition is met. Code is not straightforward. Refer to documentation.
In this case, a default profile pic was added when a user was created.

### Views

Class based views add more built in functionality.
Example:

```
class PostListView(ListView):
model = Post
template_name = "blog/home.html"
context_object_name = "posts"
ordering = ["-date_posted"]
```

You can override the default query set using a child method. In this case, we are filtering posts by user.

```
def get_queryset(self) -> QuerySet[Any]:
    user = get_object_or_404(User, username=self.kwargs.get("username"))
    return Post.objects.filter(author=user).order_by("-date_posted")
```

### Env Variables

To add environment variables, install environ

```
pip install django-environ
```
