django 
- create a repo from full gitpod template code institute
- click on gitpod btn to open gitpod workspace
- install django using " pip3 install django "
- create a django project using the django built in admin command to start a project " django-admin startproject django_todo . "
-in the directory
  * _init_.py  - a directory we can import from
  * settings.py  - global settings debug, templates,database
  * urls.py  - routing information
  * wsgi.py   - contains info that allows our webserver to communicate with our python code
* manage.py   - management utility to run our app

how to run project 
* " python3 manage.py runserver "
 - new files generated - db.sqlite3  _pycache_

django urls
create an app 
- " python3 manage.py startapp todo "

create a todo function in - views.py
def get_todo_lists(request):
    return render(request,'todo/todo_list.html')

in urls.py
 add " path('', get_todo_list, name='get_todo_list') "  to the urlpatterns

Django templates
create a "todo" folder  inside the main directory "django_todo"
inside the todo folder create a "templates" folder
inside the templates folder create "todo" folder
inside this "todo" folder create an "todo_list.html"

Migrations
run the following commands
"python3 manage.py makemigrations --dry-run"
"python3 manage.py showmigrations"
"python3 manage.py migrate --plan"
"python3 manage.py migrate"

create a super user to login ad look at the tables in the database and potentially make changes to them if we need to
" python3 manage.py createsuperuser "

username:atinos31
email:
password usuall- password without30

run app " python3 manage.py runserver"

add / admin to the url
you will be able to login
with your credentials you just created and can see from users the super user you created
