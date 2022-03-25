#mkdir django-apps
mkvirtualenv --python=python3.7 env
pip list
pip -V
#pip3 install django
pip install -U django==3.0.4
ls -lAF
deactivate
workon env
python3.7

(env) 11:50 ~ $ which django-admin.py
/home/vmarshirov/.virtualenvs/env/bin/django-admin.py

python manage.py makemigrations
python manage.py migrate


/var/www/vmarshirov_pythonanywhere_com_wsgi.py

/home/vmarshirov/django_test/mytestsite

pip install django-bootstrap4

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

pip3
 install django

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
