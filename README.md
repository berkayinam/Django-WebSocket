# Django-WebSocket
Django WebSocket Simple Example

Create virtual envoirenment for this project

#install packages


easy-install pip

python3 -m pip install virtualenv

virtualenv venv

source venv/bin/activate



pip install django

pip install channels

python -m pip install -U channels

python -m pip install -U daphne

#after installation cd /path/to/project/channels/ and migrate and create databases 


python manage.py makemigrations

python manage.py migrate

python manage.py runserver


Now, we need to create 2 users for that we will use “python manage.py createsuperuser” command which creates a superuser in the system. 


python manage.py createsuperuser

Name : user1 / pass : 123

Name : user2 / pass : 123

and after we can test WebSocket
start localhost server run python manage.py runserver and after check localhost http://localhost:8000


we must use 2 different browser, example : login for user1 Chrome and login for user2 Safari

test smth.
