# Django


## South


## django-guardian

https://github.com/django-guardian/django-guardian
https://django-guardian.readthedocs.io/

`django-guardian` is implementation of per object permissions as authorization backend which is supported sine Django 1.5. It won't work with older Django releases.

Installation

    $ sudo pip install django-guardian

Configuration

```
INSTALLED_APPS = (
...
'guardian',
)

...

AUTHENTICATION_BACKENDS = (
    'django.contrib.auth.backends.ModelBackend', # default
    'guardian.backends.ObjectPermissionBackend',
)
```

    $ python manage.py migrate

Usage

```
>>> from django.contrib.auth.models import User, Group
>>> jack = User.objects.create_user('jack', 'jack@example.com', 'topsecretagentjack')
>>> admins = Group.objects.create(name='admins')
>>> jack.has_perm('change_group', admins)
False
>>> from guardian.models import UserObjectPermissioin
>>> UserObjectPermissioin.objects.assign_perm('change_group', user=jack, obj=admins)
<UserObjectPermission: admins | jack | change_group>
>>> jack.has_perm('change_group', admins)
True
```

Admin integration

Replace `admin.ModelAdmin` with `GuardianModelAdmin` for those models which should have object permissions support within admin panel.

```
from django.contrib import admin
from myapp.models import Author
from guardian.admin import GuardianModelAdmin

# Old way:
#class AuthorAdmin(admin.ModelAdmin):
#    pass

# With object permissions support
class AuthorAdmin(GuardianModelAdmin):
    pass

admin.site.register(Author, AuthorAdmin)
```






