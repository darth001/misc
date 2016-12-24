#


##

Django supports [Oracle Database Server](http://www.oracle.com/) versions 11.2 and higher. Versions 4.3.1 or higher of the [cx_Oracle](http://cx-oracle.sourceforge.net/) Python driver is required, although we recommend version 5.1.3 or later as these versions support Python 3.

Note that due to a Unicode-corruption bug in `cx_Oracle` 5.0, that version of the driver should not be used with Django; `cx_Oracle` 5.0.1 resolved this issue, so if you'd like to use a more recent cx_Oracle, use version 5.0.1.

`cx_Oracle` 5.0.1 or greater can optionally be compiled with the `WITH_UNICODE` environment variable. This is recommended but not required.

In order for the `python manage.py migrate` command to work, your Oracle database user must have privileges to run the following commands:

* CREATE TABLE
* CREATE SEQUENCE
* CREATE PROCEDURE
* CREATE TRIGGER

To run a project's test suite, the user usually needs these additional privileges:

* CREATE USER
* ALTER USER
* DROP USER
* CREATE TABLESPACE
* DROP TABLESPACE
* CREATE SESSION WITH ADMIN OPTION
* CREATE TABLE WITH ADMIN OPTION
* CREATE PROCEDURE WITH ADMIN OPTION
* CREATE TRIGGER WITH ADMIN OPTION

Note that, while the RESOURCE role has the required CREATE TABLE, CREATE SEQUENCE, CREATE PROCEDURE AND CREATE TRIGGER privileges, and a user granted RESOURCE WITH ADMIN OPTION can grant RESOURCE, such a user cannot grant the individual privileges(e.g. CREATE TABLE), and thus RESOURCE WITH ADMIN OPTION is not usually sufficient for running tests.

Some test suites also create views; to run these, the user also needs the CREATE VIEW WITH ADMIN OPTION privilege. In particular, this is needed for Django's own test suite.

All of these privileges are included in the DBA role, which is appropriate for use on a private developers's database.

The Oracle database backend uses the SYS.DBMS_LOB and SYS.DBMS_RANDOM packages, so your user will require execute permissions on it. It's normally accessible to all users by default, but in case it is not, you'll need to grant permissions like so:

    GRANT EXECUTE ON SYS.DBMS_LOB TO user;
    GRANT EXECUTE ON SYS.DBMS_RANDOM TO user;

Connecting to the database

To connect using the service name of your Oracle database, your `settings.py` file should look something like this:

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.oracle',
            'NAME': 'xe',
            'USER': 'a_user',
            'PASSWORD': 'a_password',
            'HOST': '',
            'PORT': '',
        }
    }

In this case, you should leave both `HOST` and `PORT` empty. However, if you don't use a `tnsnames.ora` file or a similar naming method and want to connect using the SID("xe" in this example), then fill in both `HOST` and `PORT` like so:

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.oracle',
            'NAME': 'xe',
            'USER': 'a_user',
            'PASSWORD': 'a_password',
            'HOST': 'dbprod01ned.mycompany.com',
            'PORT': '1540',
        }
    }

You should either supply both `HOST` and `PORT`, or leave both as empty strings. Django will use a different connect descriptor depending on that choice.

Thread option

If you plan to run Django in a multithreaded environment(e.g. Apache using the default MPM module on any modern operating system), then you must set the `threaded` option of your Oracle database configuration to True:

    'OPTIONS': {
        'threaded': True,
    },

Failure to do this may result in crashes and other odd behavior.

INSERT ... RETURNING INTO

By default, the Oracle backend uses a `RETURNING INTO` clause to efficiently retrieve the value of an `AutoField` when inserting new rows. This behavior may result in a `DatabaseError` in certain unusual setups, such as when inserting into a remote table, or into a view with an `INSEAD OF` trigger.
The `RETURNING INTO` clause can be disabled by setting the `use_returning_into` option of the database configuration to False:

    'OPTIONS': {
        'use_returning_into': False,
    },

In this case, the Oracle backend will use a separate `SELECT` query to retrieve AutoFiled values.


Naming issues

Oracle imposes a name length limit of 30 characters. To accommodate this, the backend truncates database identifiers to fit, replacing the final four characters of the truncated name with a repeatable MD5 hash value. Additionally, the backend turns database identifiers to all-uppercase.

To prevent these transformations(this is usually required only when dealing with legacy databases or accessing tables which belong to other users), use a quoted name as the value for `db_table`.

    class LegacyModel(models.Model):
        class Meta:
            db_table = '"name_left_in_lowercase"'

    class ForeignModel(models.Model):
        class Meta:
            db_table = '"OTHER_USER"."NAME_ONLY_SEEMS_OVER_30"'

Quoted names can also be used with Django's other supported database backends; except for Oracle, however, the quotes have no effect.

When running `migrate`, an `ORA-06552` error may be encountered if certain Oracle keywords are used as the name of a model field or the value of a `db_column` option.
Django quotes all identifiers used in queries to prevent most such problems, but this error can still occur when an Oracle datatype is used as a column name. In particular, take care to avoid using the names `date`, `timestamp`, or `float` as a field name.


NULL and empty strings

Django generally prefers to use the empty string ('') rather than NULL, but Oracle treats both identically. To get around this, the Oracle backend ignores an explict `null` option on fields that have the empty string as a possible value and generates DDL as if `null=True`.
When fetching from the database, it is assumed that a `NULL` value in one of these fields reaally means the empty string, and the data is silently converted to reflect this assumption.


TextField limitations

The Oracle backend stores `TextFields` as `NCLOB` columns. Oracle imposes some limitations on the usage of such LOB columns in general:

* LOB columns may not be used as primary keys
* LOB columns may not be used in indexes
* LOB columns may not be used in a `SELECT DISTINCT` list. This means that attempting to use the `QuerySet.distinct` method on a model that includes `TextField` columns result in an `ORA-00932` error when run against Oracle. As a workaround, use the `QuerySet.defer` method in conjunction with `distinct()` to prevent `TextField` columns from being included in the `SELECT DISTINCT` list.

##

INSTALL cx_Oracle

    $ sudo pip install cx_Oracle --index https://pypi.douban.com/simple

_Collecting cx_oracle
  Downloading https://pypi.doubanio.com/packages/95/7f/3b74fe3adeb5948187b760330cb7e9175e3484bd6defdfeb9b504d71b4b3/cx_Oracle-5.2.1.tar.gz (113kB)
    100% |████████████████████████████████| 122kB 4.4MB/s 
    Complete output from command python setup.py egg_info:
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-build-dEYcbL/cx-oracle/setup.py", line 170, in <module>
        raise DistutilsSetupError("cannot locate an Oracle software " \
    distutils.errors.DistutilsSetupError: cannot locate an Oracle software installation
    
    ----------------------------------------
Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-dEYcbL/cx-oracle/_

To resolve this, download cx_Oracle, build and install it manually.

    $ cd /tmp
    $ wget https://pypi.doubanio.com/packages/95/7f/3b74fe3adeb5948187b760330cb7e9175e3484bd6defdfeb9b504d71b4b3/cx_Oracle-5.2.1.tar.gz
    $ tar xf cx_Oracle-5.2.1.tar.gz
    $ cd cx_Oracle-5.2.1

After reading instructions from the README.txt and BUILD.txt, we reallize that Oralce environment should be established completely before compiling cx_Oracle:

    $ export ORACLE_HOME=/u01/app/oracle/product/11.2.0/xe
    $ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME/lib

We also know that we must put these variables into the working shell env, either source .profile(. $HOME/.profile) or execute each export statement above from a shell individually to set these variables. If these are not added to $HOME/.profile, they will need to be manually set each time cx_Oracle is loaded into Python.

Then,

    $ python setup.py build
    $ python setup.py --user

After all these done, check it

    $ python
    $ import cx_Oracle

It is OK when no errors indicated.
