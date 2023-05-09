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
