# Deploy Django App to Heroku

Github Repo: [Djorg](https://github.com/nunulong/djorg)

Heroku App: [Djorg](https://djorg-django.herokuapp.com/)

I finally deployed the django project to heroku. I really appreciated Aaron's documents to help me successfully deploy the application. I am going to summarize the whole process.

Some errors I faced:

1.  Procfile Application Name:

How to fix: I change to the name of repo.

2.  Error while running `python manage.py collectstatic --noinput`:

How to fix: I run `heroku config:set DISABLE_COLLECTSTATIC=1`

3.  Don't forget to run `heroku run python manage.py migrate`

4.  Correctly configure the wsgi settings:

How to do:

* after installing the whitenoise package, in the settings.py file, `from whitenoise import WhiteNoise`, and add `whitenoise.middleware.WhiteNoiseMiddleware` to MIDDLEWARE, then add `STATIC_URL = '/static/'`, `STATIC_ROOT = 'static'`

* in the wsgi.py file, `from whitenoise.django import DjangoWhiteNoise`, and change to `application = DjangoWhiteNoise(get_wsgi_application())`
