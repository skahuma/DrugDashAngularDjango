# DrugDashAngularDjango

#This is Test for Using Django and Angular for the DrugDash App

 $ mkvirtualenv drf-sample<br/>
 $ pip install django==1.8.5<br/>
 $ pip install djangorestframework==3.3.0</br>
 $ django-admin startproject drf_sample</br>

##We now have a new project folder named drf_sample with the following structure:

 drf_sample/ </br>
 ├── drf_sample</br>
 │   ├── __init__.py</br>
 │   ├── settings.py</br>
 │   ├── urls.py</br>
 │   └── wsgi.py</br>
 └── manage.py</br>

##Update the Directory Structure
Let's modify the default project folder structure to support our separate applications. The modified folder structure should look like the following:

 drf_sample/ <br/>
 ├── client  <br/>
 └── server  <br/>
   ├── config <br/>
   │   ├── __init__.py<br/>
   │   ├── settings.py<br/>
   │   └── wsgi.py    <br/>
   ├── __init__.py    <br/>
   ├── manage.py      <br/>
   └── urls.py        <br/>

#Fix the Default Module Links

##In server/config/settings.py
<blockquote>
<p>ROOT_URLCONF = 'urls'
   changes to
   ROOT_URLCONF = 'server.urls'</p>
</blockquote>

<blockquote>
 <p>WSGI_APPLICATION = 'wsgi.application'<br/>
    changes to<br/>
    WSGI_APPLICATION = 'config.wsgi.application'</p>
</blockquote>
##In server/config/wsgi.py
<blockquote>
<p>os.environ.setdefault("DJANGO_SETTINGS_MODULE", "drf_sample.settings")<br/>
   changes to <br/>
   os.environ.setdefault("DJANGO_SETTINGS_MODULE", "settings")</p> 
</blockquote>
##In server/manage.py:

<blockquote>
<p> os.environ.setdefault("DJANGO_SETTINGS_MODULE", "drf_sample.settings")<br/>
   changes to <br/>
   os.environ.setdefault("DJANGO_SETTINGS_MODULE", "config.settings")</p>
</blockquote>

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
