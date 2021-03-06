# Django 
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

##### how to run project 
* " python3 manage.py runserver "
 - new files generated - db.sqlite3  _pycache_

##### django urls
 * create an app 
 - " python3 manage.py startapp todo "

##### create a todo function in - views.py
 def get_todo_lists(request):
     return render(request,'todo/todo_list.html')

##### in urls.py
 add " path('', get_todo_list, name='get_todo_list') "  to the urlpatterns

#### Django templates
 - create a "todo" folder  inside the main directory "django_todo"
 - inside the todo folder create a "templates" folder
 - inside the templates folder create "todo" folder
 - inside this "todo" folder create an "todo_list.html"

#### Migrations
run the following commands
 - "python3 manage.py makemigrations --dry-run"
 - "python3 manage.py showmigrations"
 - "python3 manage.py migrate --plan"
 - "python3 manage.py migrate"

#### create a super user /admin
- create a super user to login ad look at the tables in the database and potentially make changes to them if we need to
 - " python3 manage.py createsuperuser "
  - username:atinos31
  - email: none
  - pass usuall-  without
 * run app " python3 manage.py runserver"

add / admin to the url
you will be able to login
with your credentials you just created and can see from users the super user you created

#### MOdels
 - create model item in models.py to create tables
 - run this command
 - "python3 manage.py makemigrations"
- a new file is created in the migrations folder

 - "python3 manage.py showmigrations"
 - "python3 manage.py migrate --plan"   - to see the planned operations
 - "python3 manage.py migrate"    - to run it and apply the migration

go to admin.py
 - from .models import item
##### Register your models here.
 - admin.site.register(Item)
 - run the app " python3 manage.py runserver"
 - in the admin pannel , you can see the new items table created
   - add item "Create Item class" click on done an save

#### overide how items are displayed
 in the models.py add this inside the class item with correct indentation(4 spaces)
  "   def __str__(self): 
        return self.name "

#### Rendering data
##### views.py


# testing
- in test.py create a test class and define a function
 command - python3 manage.py test

 or more specific test commands
  * python3 manage.py test todo.test_forms
  * python3 manage.py test todo.test_forms.testItemForm
  *  python3 manage.py test todo.test_forms.testItemForm.   test_fields_are_explicit_in_form_metaclass


#### testing views
 > class TestViews(TestCase):
  
    def test_get_todo_list(self):
        response = self.client.get('/')
        self.assertEqual(response.status_code, 200)
        self.assertTemplateUsed(response, 'todo/todo_list.html')
  >
 * python3 manage.py test todo.test_views

 - ctrl / uncomments the highlighted code in py file

#### testing models
 - python3 manage.py test todo.test_models

  >
    from django.test import TestCase
     from .models import Item


    class TestModels(TestCase):

    def test_done_defaults_to_false(self):
        item = Item.objects.create(name='Test Todo Item')
        self.assertFalse(item.done)
  >

  ## coverage
    to show you how much of your code has been tested
     -  " pip3 install coverage "
     - coverage run -- source=todo manage.py test
     coverage report -to view report
     coverage html
     python3 -m http.server

 ## heroku 
 cli installation
  * windows "curl https://cli-assets.heroku.com/install.sh | sh "
  * heroku login 
   * pip3 install psyccopg2-binary
   * pip3 install gunicorn
   * pip3 freeze --local > requirements.txt