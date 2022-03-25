mkdir django-apps
#mkvirtualenv --python=python3.7 env

python -m venv env
pip -V
pip3 -V
pip list
pip3 list
pip install django-bootstrap4


. env/bin/activate
env\Scripts\activate
deactivate

pip3 install django
pip install -U django==3.0.4
pip install -U django==2.0.13
python -m django --version
django-admin --version
ls -lAF
(env) 11:50 ~ $ which django-admin.py
/home/vmarshirov/.virtualenvs/env/bin/django-admin.py


django-admin
django-admin startproject mysite
python manage.py runserver localhost:8040







python manage.py makemigrations
python manage.py migrate


+++++++++++++++++++++++++
(env) 11:50 ~ $ which django-admin.py
/home/vmarshirov/.virtualenvs/env/bin/django-admin.py
https://www.pythonanywhere.com/user/vmarshirov/webapps/#tab_id_vmarshirov_pythonanywhere_com
Virtualenv:
Use a virtualenv to get different versions of flask, django etc from our default system ones. More info here. You need to Reload your web app to activate it; NB - will do nothing if the virtualenv does not exist.
Enter path to a virtualenv, if desired
/home/vmarshirov/.virtualenvs/env

(env) 12:04 ~ $ pwd
/home/vmarshirov
Code:
What your site is running.
Source code:
Enter the path to your web app source code
/home/vmarshirov 
============================

107  . env/bin/activate
108  . virtualenvs/
109  workon myproject
110 pip3 install django

=====================
model
=========================

import datetime
from django.db import models
from django.utils import timezone

# Create your models here.

=======================
https://www.youtube.com/watch?v=w4nrT7emiVc&list=PLpd6jV8ypKS4GW7G0twauncmr4x7d0-SI&index=4&t=4s
--------------------
2:04 Установка
4:08 Создаём проект
4:54 Обзор файлов проекта
9:27 Запуск сервера
12:15 Создаём приложение
13:10 Настройка проекта(settings.py)
14:20 Обзор структуры приложения
17:15 Маршруты (urls.py)
24:35 Модели
34:35 Миграции (обзор)
35:52 Создание миграций и прописываем приложение в настройках проекта (сперва прописываем потом миграция)
37:08 Применение миграции + обзорно возможность правки миграций
38:10 Сама команда применить миграции
40:26 Python shell + немного ORM (работа с БД)
55:06 Админка
56:31 Локализация сайта (settings.py)
56:50 Добавление в админку CRUD (Create Read Update Delete) для ваших моделей
58:40 Настройка отображения вашего приложения в Админке
1:01:00 Красивая Админка (строннний пакет grappelli)
1:06:30 Templates + патч в settings.py, чтобы django находил наши шаблоны
1:09:00 Шаблонизатор + ORM (работа с БД)
1:18:50 Псевдонимы ссылок
1:22:50 Добавление комментариев (связанные таблицы)
--------------------

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')
    def __str__(self):
        return self.question_text

    def was_published_recently(self):
        return self.pub_date >= timezone.now() - datetime.timedelta(days=5)

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
    def __str__(self):
        return self.choice_text

    def was_published_recently(self):
        return self.pub_date <= timezone.now() - datetime.timedelta(days=3)



python manage.py makemigrations polls
python manage.py sqlmigrate polls 0001
python manage.py migrate


python manage.py shell
from polls.models import Question, Choice
a = Question.objects.all()
a = Question.objects.get(id = 1)
a.id
a.pub_date

a.was_published_recently()
Question.objects.filter(id = 1)
pub_date.objects.filter(id = 1)
Question.objects.filter(question_text__startswith = "Q")
a.question_text = "abc"
a.save()
Question.objects.filter(question_text__startswith = "a")

from django.utils import timezone
current_year = timezone.now().year
current_year
Question.objects.filter( pub_date__year = current_year)

Question.objects.get(id = 2) нет
но можно будет использовать для обработки исключений
polls.models.Question.DoesNotExist: Question matching query does not exist.

a.choice_set.all()
<QuerySet [<Choice: Not much>]>
a.choice_set.create(choice_text = "абв", votes = 5)
a.choice_set.all()
<QuerySet [<Choice: абв>]>

a.choice_set.count()
a.choice_set.get(id = 2)
dl = a.choice_set.all()
dl.delete()
a.choice_set.all()
<QuerySet []>


=================
admin
================
python manage.py createsuperuser

ru-RU
TIME_ZONE = 'Europe/Moscow' 

/home/vmarshirov/mysite/polls/admin.py
from django.contrib import admin
from .models import Question, Choice
admin.site.register(Question)
admin.site.register(Choice)


-------------
/home/vmarshirov/mysite/polls/apps.py


=====================
https://django-grappelli.readthedocs.io/en/latest/quickstart.html

/home/vmarshirov/mysite/mysite/settings.py 
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(PROJECT_ROOT,'static') - в конце файла

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/3.0/howto/static-files/

#STATIC_URL = '/static/'
#STATIC_ROOT = os.path.join(PROJECT_ROOT,'static')

STATIC_URL = 'https://www.pythonanywhere.com/user/vmarshirov/files/home/vmarshirov/mysite/mysite/static'
STATIC_ROOT = '/home/vmarshirov/mysite/mysite/static'





https://developer.mozilla.org/ru/docs/Learn/Server-side/Django/development_environment
https://www.stanleyulili.com/django/how-to-install-django-on-windows/#step-4---create-a-project-directory
------------------------------
https://www.digitalocean.com/community/tags/django
https://www.digitalocean.com/community/tutorials/how-to-install-django-and-set-up-a-development-environment-on-ubuntu-16-04
https://docs.djangoproject.com/en/2.0/intro/tutorial01/

https://stackoverflow.com/questions/9628885/django-data-flow-diagrams

python -V
pip3 list

mkdir django-apps/ 
cd django-apps/
virtualenv env - только при начальной установке
. env/bin/activate



pip install django - только при начальной установке 
django-admin --version
django-admin startproject testsite - только при начальной установке
cd testsite
vim testsite/settings.py   - ALLOWED_HOSTS = ['37.139.11.127'] -только при начальной установке
python manage.py createsuperuser     g06u40 eH..L
------------------------

python manage.py startapp polls

каждый раз при корректировке
python manage.py migrate
python manage.py runserver 37.139.11.127:8001  8000-8090 - испольовать последние цифры логина
37.139.11.127:8001  - в браузере
http://37.139.11.127:8001/polls/
http://37.139.11.127:8001/admin/
deactivate  - завершение работы


python manage.py makemigrations

https://docs.djangoproject.com/en/2.0/intro/tutorial01/
e...7L7L


------------------------------

pip3 install django

python -V
py -3 -V

mkdir django_project
cd  django_project
python -m venv venv
venv\Scripts\activate
pip install django
django-admin startproject testsite
cd testsite
python manage.py  runserver

python -m venv venv
============================
1
python -m venv pollster
venv\Scripts\activate
pip install django

django-admin startproject pollster
cd pollster
python manage.py runserver 8081
http://127.0.0.1:8081/


cd ../
python manage.py migrate
=========================

python manage.py  startapp polls

pip3  install virtualenvwrapper-win
mkvirtualenv  my_django_environment


python -m pip install --upgrade pip
mkdir django_project
PS C:\Users\Username\django_project>
python -m venv venv
(venv)
 PS C:\Users\Stanley\django_project>
(venv)> pip install django
(venv)> pip install django==2.1
(venv)> django-admin startproject testsite
(venv)> python manage.py runserver
http://127.0.0.1:8000/


cd  mytestsite
python3 manage.py runserver
http://127.0.0.1:8000/

------------------
models.py

class Question(models.Model):
    question_text = models.CharField(_("CharField"), max_length=50)
    pub_date = models.DateField(_("DataPublish  "), auto_now=False, auto_now_add=False)
    def __str__(self):
        return self.question_text

class Choice (models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(_("abc1"), max_length=50)
    votes = models.IntegerField(default=0)

    def __str__(self):
        return self.choice_text

======================
Установка

https://www.digitalocean.com/community/tags/django

https://www.digitalocean.com/community/tutorials/how-to-install-django-and-set-up-a-development-environment-on-ubuntu-16-04

mkdir django-apps
cd django-apps
virtualenv env
. env/bin/activate
pip install django
django-admin --version
??? sudo ufw allow 8000
django-admin startproject testsite
cd testsite

. env/bin/activate
cd testsite/
vim settings.py
python manage.py runserver 37.139.11.127:8001
deactivate
