# Django


## South

__South has been deprecated.__
From Django 1.7 upwards, migrations are built into the core of Django.

https://south.readthedocs.io/

The First Migration

    $ ./manage.py schemamigration app --initial
    $ ./manage.py migrate app

Changing the model

    $ ./manage.py schemamigration app --auto
    $ ./manage.py migrate app

Defaults

    $ ./manage.py schemamigration app --auto
    $ ? The field 'Modle.Field' does not have a default specified, yet is NOT NULL.
    $ ? Since you are adding or removing this field, you MUST specify a default
    $ ? value to use for existing rows. Would you like to:
    $ ? 1. Quit now, and add a default to the field in models.py
    $ ? 2. Specify a one-off value to use for existing columns now
    $ ? Please select a choice:
    ...

    $ ./manage.py migrate app

Uniques

    $ ./manage.py schemamigration app --auto
    $ ./manage.py migrate app

ManyToMany fields

Custom fields

Iteratively working on a migration

    $ ./manage.py schemamigration app --auto --update
    $ ./manage.py migrate app

Listing current migrations

    $ ./manage.py migrate --list

Data migrations

    $ ./manage.py schemamigraiton app --auto
    $ ./manage.py datamigration app custom_migration


```
# xxxx_custom_migration.py
def forwards(self, orm):
    ...

def backwards(self, orm):
    raise Runtimeerror("Cannot reverse this migration.")
```

    $ ./manage.py schemamigration app --auto
    $ ./manage.py migrate app

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






