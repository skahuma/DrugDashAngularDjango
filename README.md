# DrugDashAngularDjango

#This is Test for Using Django and Angular for the DrugDash App

> $ mkvirtualenv drf-sample
> $ pip install django==1.8.5
> $ pip install djangorestframework==3.3.0
> $ django-admin startproject drf_sample</p>
##We now have a new project folder named drf_sample with the following structure:

> drf_sample/
> ├── drf_sample
> │   ├── __init__.py
> │   ├── settings.py
> │   ├── urls.py
> │   └── wsgi.py
> └── manage.py

##Update the Directory Structure
Let's modify the default project folder structure to support our separate applications. The modified folder structure should look like the following:

> drf_sample/
> ├── client
> └── server
>   ├── config
>   │   ├── __init__.py
>   │   ├── settings.py
>   │   └── wsgi.py
>   ├── __init__.py
>   ├── manage.py
>   └── urls.py

#Fix the Default Module Links

##In server/config/settings.py

> ROOT_URLCONF = 'urls'
>>    changes to
> ROOT_URLCONF = 'server.urls'</p>

>  WSGI_APPLICATION = 'wsgi.application'
>>    changes to
>  WSGI_APPLICATION = 'config.wsgi.application'</p>

##In server/config/wsgi.py

>   os.environ.setdefault("DJANGO_SETTINGS_MODULE", "drf_sample.settings")
>>   changes to
>   os.environ.setdefault("DJANGO_SETTINGS_MODULE", "settings")</p>

##In server/manage.py:

>  os.environ.setdefault("DJANGO_SETTINGS_MODULE", "drf_sample.settings")
>>    changes to
>   os.environ.setdefault("DJANGO_SETTINGS_MODULE", "config.settings")</p>


##$ python server/manage.py runserver

Performing system checks...

System check identified no issues (0 silenced).

You have unapplied migrations; your app may not work properly until they are applied.
Run 'python manage.py migrate' to apply them.

February 17, 2017 - 13:26:29
Django version 1.8, using settings 'config.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.

Perfect! Our project is now ready to support both server and client code.
