# Blackjack Tutorial
---
### Requirements:
- Python 3.6
  - virtualenv
- Django 2.0.7
---
### Prerequisites:
- Python
- Django
  - Models
    - User from django.contrib.auth.models
    - OneToOneField modeling
  - Forms
  - Urlpatterns
  - TemplateView from django.views.generic
  - messages from django.contrib
- HTML
- CSS
- Bootstrap 4
- JavaScript
---
### Windows step by step guide

#### 1. Create virtual environment using Python's virtualenv
First let's check the Python version.
Open your command prompt terminal or **CMD**. While holding windows logo press **R** to open Run window. Now type cmd and hit enter.
In your command prompt terminal or **CMD** type **python -V** with capital V:
```
C:\Users\Goran>python -V
```
You should get output like:
```
Python 3.6.5
```

Now enter the following command:
```
C:\Users\Goran>pip install virtualenv
```
or
```
C:\Users\Goran>pip3 install virtualenv
```
or
```
C:\Users\Goran>python -m pip install virtualenv
```
> Note that instead Goran there will be your PC username.

Next create directory where we will store our project and virtualenv files using **mkdir**:
```
C:\Users\Goran>mkdir blackjack_project
```
Check to see is blackjack_project created with command **dir**:
```
C:\Users\Goran>dir
```
You should get output similar to this:
```
23/07/2018  10:24    <DIR>          .
23/07/2018  10:24    <DIR>          ..
23/07/2018  12:13    <DIR>          blackjack_project
18/04/2018  07:53    <DIR>          Contacts
23/07/2018  11:29    <DIR>          Desktop
16/05/2018  15:40    <DIR>          Documents
23/07/2018  10:15    <DIR>          Downloads
```
Change directory to blackjack_project using cd:
```
C:\Users\Goran>cd blackjack_project
C:\Users\Goran\blackjack_project>
```
Now let's create the virtual environment using the **virtualenv**:
```
C:\Users\Goran\blackjack_project>virtualenv blackjackenv
```
Now run command **blackjackenv\Scripts\activate**:
```
C:\Users\Goran\blackjack_project>blackjackenv\Scripts\activate
```
If all went good command line should look like this:
```
(blackjackenv) C:\Users\Goran\blackjack_project>
```
> Note the (blackjackenv) before C:\ which means that you are inside virtual environment.
---
#### 2. Install django inside virtual environment
Run the command **pip install django==2.0.7**:
```
(blackjackenv) C:\Users\Goran\blackjack_project>pip install django==2.0.7
```
If you get Successfully installed django-2.0.7 message let's create django project.
* * *
#### 3. Start django project
Run the command **django-admin startproject game**:
```
(blackjackenv) C:\Users\Goran\blackjack_project>django-admin startproject game
```
Run **dir** to see if it is created:
```
(blackjackenv) C:\Users\Goran\blackjack_project>dir
```
And you should get output like this:
```
23/07/2018  12:32    <DIR>          .
23/07/2018  12:32    <DIR>          ..
23/07/2018  12:17    <DIR>          blackjackenv
23/07/2018  12:32    <DIR>          game
```
Let's **cd** into game.  You can autocomplete path names by using **Tab** key like for example type
**cd g** and press **Tab**
```
(blackjackenv) C:\Users\Goran\blackjack_project>cd game
```
Run **dir** again:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>dir
```
Output should be like following: 
```
23/07/2018  12:32    <DIR>          .
23/07/2018  12:32    <DIR>          ..
23/07/2018  12:32    <DIR>          game
23/07/2018  12:32               551 manage.py
```
#### 4. Create django app with name blackjack
Now let's create django app with command **startapp**:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py startapp blackjack
```
Run **dir** to check the changes:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>dir
```
You should see the blackjack folder in the output:
```
23/07/2018  13:03    <DIR>          .
23/07/2018  13:03    <DIR>          ..
23/07/2018  13:03    <DIR>          blackjack
23/07/2018  13:03    <DIR>          game
23/07/2018  12:32               551 manage.py
```
We will now put the app in the **game\settings .py**.
Type **cd game**:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd game
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>notepad settings.py
```
Under **INSTALLED_APPS** add 'blackjack' at bottom. It should look like this and hit save (Ctrl + S):
```python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blackjack',
]
```
We will now install the app with the command **migrate**. 
In the cmd window type **cd..** to go back for one directory:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>cd..
```
And then type: 
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py migrate
```
You should get:
```
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK
  
  (blackjackenv) C:\Users\Goran\blackjack_project\game>
```
This shows that app is successfully installed. 
Now let's just test run the django server to check if everything is well to move on:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py runserver
```
You should get:
```
Performing system checks...

System check identified no issues (0 silenced).
July 23, 2018 - 14:07:29
Django version 2.0.7, using settings 'game.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
This means that we are ready for next part. Hit Ctrl + C to stop the server.
* * *
#### 5. Creating base templates and adding TEMPLATES_DIR to settings
In cmd window you should be at the path:
```
 (blackjackenv) C:\Users\Goran\blackjack_project\game>
```
Type **mkdir templates** to create templates folder:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>mkdir templates
```
Type **dir** to ensure that it is created in right path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>dir
```
And you should have output like this:
```
23/07/2018  14:35    <DIR>          .
23/07/2018  14:35    <DIR>          ..
23/07/2018  13:03    <DIR>          blackjack
23/07/2018  14:05           131,072 db.sqlite3
23/07/2018  13:03    <DIR>          game
23/07/2018  12:32               551 manage.py
23/07/2018  14:35    <DIR>          templates
```
Let's now enter the templates folder to create blank html files with command **cd. > filename**:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd templates
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>cd. > base.html
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>cd. > index.html
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>cd. > thanks.html
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>cd. > messages.html
```
And now just type **dir** to check if files are created:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>dir

 Directory of C:\Users\Goran\blackjack_project\game\templates

23/07/2018  14:49    <DIR>          .
23/07/2018  14:49    <DIR>          ..
23/07/2018  14:47                        362 base.html
23/07/2018  14:48                        410 index.html
23/07/2018  14:49                        510 messages.html
23/07/2018  14:48                        459 thanks.html
```
Now let's create templates under blackjack app.
You should be at path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>
```
Let's head to blackjack and create needed files and folders:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>mkdir templates\blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>cd templates\blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>cd. > index.html
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>cd. > signup.html
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>cd. > login.html
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>dir

 Directory of C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack

23/07/2018  15:58    <DIR>          .
23/07/2018  15:58    <DIR>          ..
23/07/2018  15:57               383 index.html
23/07/2018  15:58               480 login.html
23/07/2018  15:57               432 signup.html
```
We will fill all of these files with code later, now we are just creating the files and folders needed for this project.
Now we need to tell django where to search for templates through game\settings:
``` 
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>cd ..\..\..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd game
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>notepad settings.py
```
Under the variable **BASE_DIR**:
```python
# Build paths inside the project like this: os.path.join(BASE_DIR, ...)
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
```
Add following line of code which will merge templates path with base path:
```python
TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')
``` 
It should look like:
```python
# Build paths inside the project like this: os.path.join(BASE_DIR, ...)
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')
```
Now under TEMPLATES inside DIRS add **TEMPLATE_DIR** which should look like this:
```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [TEMPLATE_DIR], # Here we add the TEMPLATE_DIR inside [ ]
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

```
Hit save (Ctrl + S) and go back to terminal. Time to create STATIC FILES.
* * *
#### 6. Creating STATIC files
You should be at path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>
```
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>mkdir static\game
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd static\game
```
Copy **static** folders from pp module 9 downloadable content inside path:
```
 C:\Users\Goran\blackjack_project\game\static\game>
```
It contains 4 folders: **css**,**images**,**js**,**sounds**. We will tweak css and js in later steps.

Let's add static files path with variable STATICFILES_DIRS in settings. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\static\game>cd ..\..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd game
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>notepad settings.py
```
Add this line of code at the bottom under STATIC_URL:
```python
STATICFILES_DIRS = [os.path.join(BASE_DIR,'static')]
```
Save the file Ctrl + S and go back to terminal.
* * * 
#### 7. Creating BASE views
You should be at path::
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>
```
Now type the following to create and open the base views .py file:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>cd. > views.py
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>notepad views.py
```
Inside views .py we will import TemplateView and render:
```python
from django.views.generic import TemplateView
from django.shortcuts import render
```
Next create the home page view using render:
```python
def Home(request):
    return render(request, 'index.html')
```
Now let's create thanks page when user log out with class based TemplateView:
```python
class ThanksPage(TemplateView):
    template_name = 'thanks.html'
```
Your views .py now should look like this:
```python
from django.views.generic import TemplateView
from django.shortcuts import render

def Home(request):
    return render(request, 'index.html')

class ThanksPage(TemplateView):
    template_name = 'thanks.html'
```
Save the file (Ctrl + S) and let's create base urls now.
* * *
#### 8. Create BASE urls
You should be at path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>
```
Now type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>notepad urls.py
```
First we will import include as we are going to create and include blackjack app urls:
```python
from django.urls import path, include  # we are extending existing line with include
```
Next we import base views from same folder:
```python
from . import views
```
Now let's create paths for home view above the admin path:
```python
urlpatterns = [
    path('', views.Home, name='home'),
    path('admin/', admin.site.urls),
]
```
Next we create the thanks view path under the line home path:
```python
urlpatterns = [
    path('', views.Home, name='home'),
    path('thanks/',views.ThanksPage.as_view(),name='thanks'),
    path('admin/', admin.site.urls),
]
```
And finally under home path we include the blackjack urls which we will create in next step:
```python
urlpatterns = [
    path('', views.Home, name='home'),
    path('blackjack/', include('blackjack.urls')),
    path('thanks/',views.ThanksPage.as_view(),name='thanks'),
    path('admin/', admin.site.urls),
]
```
Now urls should look like this:
```python
from django.contrib import admin
from django.urls import path, include
from . import views

urlpatterns = [
    path('', views.Home, name='home'),
    path('blackjack/', include('blackjack.urls')),
    path('thanks/',views.ThanksPage.as_view(),name='thanks'),
    path('admin/', admin.site.urls),
]
```
Save the file (Ctrl + S) and let's move to the blackjack app.
* * *
#### 9. Create the BLACKJACK app urls
You should be at path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>
```
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>cd. > urls.py
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad urls.py
```
First make the imports:
```python
from django.urls import path
from . import views
```
Now we will import views from django.auth. They are already created for us (thanks django) and this is the reason why we are using frameworks, so we don't need to recreate existing classes and functions. Just pay attention, here I'm using **as auth_views** so there is no conflict with our blackjack view.
```python
from django.contrib.auth import views as auth_views
```
Next we create an variable **app_name** so we can call these urls through html templates:
```python
app_name = 'blackjack'
```
Add the urlpatterns:
```python
urlpatterns = [
    path('', views.index, name='index'),
    path('login/',auth_views.LoginView.as_view(template_name='blackjack/login.html'), name='login'),
    path('logout/',auth_views.LogoutView.as_view(),name='logout'),
    path('signup/',views.SignUp, name='signup'),
    path('update_game/', views.update_game, name='update_game'),
]
```
And your blackjack app urls should look like this:
```python
from django.urls import path
from . import views
from django.contrib.auth import views as auth_views

app_name = 'blackjack'

urlpatterns = [
    path('', views.index, name='index'),
    path('login/',auth_views.LoginView.as_view(template_name='blackjack/login.html'), name='login'),
    path('logout/',auth_views.LogoutView.as_view(),name='logout'),
    path('signup/',views.SignUp, name='signup'),
    path('update_game/', views.update_game, name='update_game'),
]
```
Let's prepare the views with empty functions and to test run the server. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad views.py
```
Under the line:
```python
# Create your views here.
```
Create empty function based views:
```python
def index(request):
    return render(request)
  
def SignUp(request):
    return render(request)

def update_game(request):
    return render(request)
```
Save the file (Ctrl + S) and go back to terminal. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py runserver
```
If you get output like:
```
Performing system checks...

System check identified no issues (0 silenced).
July 24, 2018 - 10:58:04
Django version 2.0.7, using settings 'game.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
Then you are ready to move on to create blackjack models. Hit Ctrl + C to stop the server.
* * *
#### 10. Creating blackjack models
You should be on path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>
```
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad models.py
```
Let's add the required import for auth User:
```python
from django.contrib.auth.models import User
```
Create the user model:
```python
# Create auth user model
class User(User):
    
    def __str__(self):
        return self.username
```
It is easy as that.
Now we will create game fields and will make **OneToOneField** relation with user model:
```python
# Extending user model with OneToOne relation
class Game(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    money = models.IntegerField(default=0)
    wins = models.IntegerField(default=0)
    losses = models.IntegerField(default=0)
    draws = models.IntegerField(default=0)
    
    # Method to show users game info in admin panel
    def __str__(self):
        return "{}'s Game Info".format(self.user)
```
Your blackjack models should now look like this:
```python
from django.db import models
from django.contrib.auth.models import User

# Create your models here.

# Create auth user model
class User(User):

    def __str__(self):
        return self.username

# Extending user model with OneToOneField relation
class Game(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    money = models.IntegerField(default=0)
    wins = models.IntegerField(default=0)
    losses = models.IntegerField(default=0)
    draws = models.IntegerField(default=0)
    
    # Method to show users game info in admin panel
    def __str__(self):
        return "{}'s Game Info".format(self.user)
```
Save the file Ctrl + S. Go back to terminal and  let's register the Game model in admin. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad admin.py
```
And add the code:
```python
from . import models

# Register your models here.
admin.site.register(models.Game)
```
Save the file Ctrl + S.
Now let's create the **Forms**.
* * *
#### 11. Creating blackjack forms
Let's start by creating forms .py file:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>cd. > forms.py
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad forms.py
```
First we add the imports:
```python
from .models import User, Game
from django.contrib.auth.forms import UserCreationForm
from django import forms
```
The **UserCreationForm** will save us from writing around 30 lines of code. For example this is how it looks:
```python
class UserCreationForm(forms.ModelForm):
    """
    A form that creates a user, with no privileges, from the given username and
    password.
    """
    error_messages = {
        'password_mismatch': _("The two password fields didn't match."),
    }
    password1 = forms.CharField(
        label=_("Password"),
        strip=False,
        widget=forms.PasswordInput,
        help_text=password_validation.password_validators_help_text_html(),
    )
    password2 = forms.CharField(
        label=_("Password confirmation"),
        widget=forms.PasswordInput,
        strip=False,
        help_text=_("Enter the same password as before, for verification."),
    )

    class Meta:
        model = User
        fields = ("username",)
        field_classes = {'username': UsernameField}

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        if self._meta.model.USERNAME_FIELD in self.fields:
            self.fields[self._meta.model.USERNAME_FIELD].widget.attrs.update({'autofocus': True})

    def clean_password2(self):
        password1 = self.cleaned_data.get("password1")
        password2 = self.cleaned_data.get("password2")
        if password1 and password2 and password1 != password2:
            raise forms.ValidationError(
                self.error_messages['password_mismatch'],
                code='password_mismatch',
            )
        return password2

    def _post_clean(self):
        super()._post_clean()
        # Validate the password after self.instance is updated with form data
        # by super().
        password = self.cleaned_data.get('password2')
        if password:
            try:
                password_validation.validate_password(password, self.instance)
            except forms.ValidationError as error:
                self.add_error('password2', error)

    def save(self, commit=True):
        user = super().save(commit=False)
        user.set_password(self.cleaned_data["password1"])
        if commit:
            user.save()
        return user
```
And we use all of that with one import.
Now let's create the User Sign Up form:
```python
# Sign Up form
class UserCreateForm(UserCreationForm):
     
    class Meta:
        model = User
        fields = ('username','email','password1','password2',)
```
Fields 'username','email' comes from User and 'password1','password2' from UserCreationForm.
And now we will create form for updating game score:
```python
# Game update form
class GameUpdateForm(forms.ModelForm):
    class Meta:
        fields = ('user','money','wins','losses', 'draws')
        model = Game
        # I made user field read only just for you don't mess the database while testing the form we will remove it later
        widgets = {
            'user': forms.TextInput(attrs={'readonly': 'readonly'}),
        }
  ```
We will come back later to this form to make fields but for now leave it as it is.
Time to create views.
* * *
#### 12. Creating blackjack views
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad views.py
```
Make the imports:
```python
from django.shortcuts import render, redirect
from .models import Game, User
from django.contrib.auth.decorators import login_required
from .forms import UserCreateForm, GameUpdateForm
from django.contrib import messages
```
Next create the index view using login_required decorator so only logged in users can access that page:
```python
# Visitor needs to be logged in to access this page
@login_required
def index(request):
    instance = Game.objects.filter(user=request.user).first()
    if request.user.is_authenticated and request.method == 'GET':
        form = GameUpdateForm(instance=instance)
        games = Game.objects.get(id=request.user.id)
        # We render games as we will use it in template to show scores and form to update scores
        return render(request, 'blackjack/index.html', {'games': games, 'form': form})
```
Next create the Sign Up view:
```python
# Sign Up view
def SignUp(request):
    if request.method == 'POST':
        form = UserCreateForm(request.POST)
        if form.is_valid():
            # Create user
            user = form.save(commit=False)
            # Save user to database
            user.save()
            # Create game score fields
            Game.objects.create(user=user)
            # Save game score fields for created user to database
            user.game.save()
            msg_conf = 'Account successfully created!'
            messages.success(request, msg_conf)
            return redirect('/blackjack/login/')
    else:
        # If request method is GET just render the UserCreateForm
        form = UserCreateForm()
    # We render the sign up form
    return render(request, 'blackjack/signup.html', {'form': form})
```
And create the update game view for updating game scores:
```python
# Update scores view
def update_game(request):
    instance = Game.objects.filter(user=request.user).first()
    if request.method == 'POST':
        form = GameUpdateForm(request.POST, instance=instance)
        if form.is_valid():
            # Update scores
            score = form.save(commit=False)
            # Save scores to database
            score.save()
    return redirect('/blackjack')
```
We are done with creating views. Let's check if your views looks like this:
```python
from django.shortcuts import render, redirect
from .models import Game, User
from django.contrib.auth.decorators import login_required
from .forms import UserCreateForm, GameUpdateForm
from django.contrib import messages
# Create your views here.


# Visitor needs to be logged in to see this page
@login_required
def index(request):
    instance = Game.objects.filter(user=request.user).first()
    if request.user.is_authenticated and request.method == 'GET':
        form = GameUpdateForm(instance=instance)
        games = Game.objects.get(id=request.user.id)
        return render(request, 'blackjack/index.html', {'games': games, 'form': form})

# Sign Up view
def SignUp(request):
    if request.method == 'POST':
        form = UserCreateForm(request.POST)
        if form.is_valid():
            # Create user
            user = form.save(commit=False)
            # Save user to database
            user.save()
            # Create game score fields
            Game.objects.create(user=user)
            # Save game score fields fosr created user to database
            user.game.save()
            msg_conf = 'Account successfully created!'
            messages.success(request, msg_conf)
            return redirect('/blackjack/login/')
    else:
        # If request method is GET just render the UserCreateForm
        form = UserCreateForm()
    return render(request, 'blackjack/signup.html', {'form': form})

# Update scores view
def update_game(request):
    instance = Game.objects.filter(user=request.user).first()
    if request.method == 'POST':
        form = GameUpdateForm(request.POST, instance=instance)
        if form.is_valid():
            # Update scores
            score = form.save(commit=False)
            # Save scores to database
            score.save()
    return redirect('/blackjack')
```
* * *
#### 13. Filling the base template files with code
If you are in right path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>
```
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd templates
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>notepad base.html
```
And enter the following code:
```html
<!DOCTYPE html>
{% load staticfiles %}
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.0/css/bootstrap.min.css">
    <link rel="stylesheet" href="{% static 'game/css/style.css'%}">
  </head>
    <body>

		<nav class="navbar navbar-expand-lg navbar-light bg-light" role="navigation" id="navbar">
			<div class="container mynav">
				<a class="navbar-brand" href="{% url 'home' %}">BLACKJACK</a>
				<ul class="nav navbar-nav ml-auto">
				{% if user.is_authenticated %}
					<li><a href="{% url 'blackjack:index' %}">Play</a></li>
					<li><a href="{% url 'blackjack:logout' %}">Log out</a></li>
				{% else %}
					<li><a href="{% url 'blackjack:login' %}">Log in</a></li>
					<li><a href="{% url 'blackjack:signup' %}">Sign up</a></li>
				{% endif %}
				</ul>
			</div>
		</nav>
            
        <div class="container">
			<div class="row">
				<div class="col-md-12 text-center">
					{% include 'messages.html' %}
				</div>
            </div>
                {% block content %}

                {% endblock %}

        </div>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js" integrity="sha384-smHYKdLADwkXOn1EmN1qk/HfnUcbVRZyYmZ4qpPea6sjB/pTJ0euyQp0Mk8ck+5T" crossorigin="anonymous"></script>
        <script src="{% static 'game/js/script.js'%}"></script>
        {% block javascript %}{% endblock %}
    </body>
</html>
```
At line 18 **{% if user.is_authenticated %}** we check if user is logged in and if True then show links Play and Log In, line 21 **{% else %}** will show Log In and Sign up if user is not logged in and with line 24 **{% endif %}** we close the if statement as indentation has no role in html except for keeping the code organized.
At line 32 we include the messages .html which are in same folder as base .html.
All other templates will be between lines 35 **{% block content %}** and 37 **{% endblock %}** as we will extend base .html to them.
We will use code at line 43 **{% block javascript %}{% endblock %}** to add some JavaScript in other templates.
Save the file Ctrl + S and go back to terminal.
Now type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>notepad messages.html
```
And add the code bellow:
```html
{% if messages %}
  {% for message in messages %}
    <div class="alert {{ message.tags }} alert-dismissible" role="alert">
      <a class="close" data-dismiss="alert">×</a>
      {{ message }}
    </div>
  {% endfor %}
{% endif %}
```
This code is to show error or success messages if there are any.
Save the file Ctrl + S and go back to terminal.
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>notepad index.html
```
Place this code inside:
```html
{% extends "base.html" %}
{% block content %}
  <div class="index" style="margin-top:200px; color:white;">
    <h1>Blackjack Game</h1>
    <h2>Log In or Sign Up to get started!</h2>
  </div>
{% endblock %}
```
This is the home page and is extending base .html.
Save the file Ctrl + S
And now type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>notepad thanks.html
```
And put this code inside:
```html
{% extends "base.html" %}
{% block content %}
  <h1 style="margin-top:200px;">Thanks for playing!</h1>
  <h1>Come back soon!</h1>
{% endblock %}
```
This page will be shown when user logs out.

Now let's add MESSAGE_TAGS,  LOGIN_REDIRECT_URL and LOGOUT_REDIRECT_URL at our settings file.
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\templates>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd game
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>notepad settings.py
```
At the bottom place the following:
```python
# Making messages looks nice if using bootstrap
MESSAGE_TAGS = {
    messages.DEBUG: 'alert-info',
    messages.INFO: 'alert-info',
    messages.SUCCESS: 'alert-success',
    messages.WARNING: 'alert-warning',
    messages.ERROR: 'alert-danger',
}

LOGIN_REDIRECT_URL = '/blackjack'
LOGOUT_REDIRECT_URL = '/thanks'
```
Your settings file should look like this:
```python
"""
Django settings for game project.
Generated by 'django-admin startproject' using Django 2.0.7.
For more information on this file, see
https://docs.djangoproject.com/en/2.0/topics/settings/
For the full list of settings and their values, see
https://docs.djangoproject.com/en/2.0/ref/settings/
"""

import os
from django.contrib.messages import constants as messages
# Build paths inside the project like this: os.path.join(BASE_DIR, ...)
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')

# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/2.0/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = '^hk47(a0#!7dl78=3f-t&f7m50ji=xkgpcyj=6z4z6=$s#wyaq'

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = []

# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blackjack',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'game.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [TEMPLATE_DIR],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'game.wsgi.application'


# Database
# https://docs.djangoproject.com/en/2.0/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}


# Password validation
# https://docs.djangoproject.com/en/2.0/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]

# Internationalization
# https://docs.djangoproject.com/en/2.0/topics/i18n/

LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_L10N = True

USE_TZ = True


# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/2.0/howto/static-files/

STATIC_URL = '/static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR,'static')]

# Making messages looks nice if using bootstrap
MESSAGE_TAGS = {
    messages.DEBUG: 'alert-info',
    messages.INFO: 'alert-info',
    messages.SUCCESS: 'alert-success',
    messages.WARNING: 'alert-warning',
    messages.ERROR: 'alert-danger',
}

LOGIN_REDIRECT_URL = '/blackjack'
LOGOUT_REDIRECT_URL = '/thanks'
```
Save the file Ctrl + S and go back to terminal. Our settings file is now ready for local environment.
Now let's fill the blackjack templates.
* * *
#### 14. Filling the blackjack template files with code
You should be at path:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>
```
Now type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\game>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd blackjack\templates\blackjack
```
Now lets open blackjack's index .html:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>notepad index.html
```
And place this code inside it:
```html
{% extends "base.html" %}
{% block content %}
    <div class="container">
        <div class="row" style="padding:20px;">
            <div class="col-md-12 text-center">
                <h1>Player:  {{ user.username }}</h1>
            </div>
        </div>
    </div>
    <form action='update_game/' method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <!-- This button will be hidden later when we hide the form-->
        <button type="submit" id="update_button">Submit</button> 
    </form>
    <div class="container-5">
        <h2>Money: $<span id="money">{{ games.money }}</span></h2>
        <h2><span id='blackjack-result'>Let's play</span></h2>
        <div class="flex-blackjack-row-1">

            <div id="your-box">
                <h2>You: <span id="your-blackjack-score">0</span></h2>
            </div>

            <div id="dealer-box">
                <h2>Dealer: <span id="dealer-blackjack-score">0</span></h2>
            </div>

        </div>

        <div class="flex-blackjack-row-2">
            <div>
                <button class='btn-lg btn-primary mr-2' id='blackjack-hit-button'>Hit</button>
                <button class='btn-lg btn-warning mr-2' id='blackjack-stand-button'>Stand</button>
                <button class='btn-lg btn-danger mr-2' id='blackjack-deal-button'>Deal</button>
            </div>
        </div>

        <div class="flex-blackjack-row-3">
            <table>
                <tr>
                    <th>Wins</th>
                    <th>Losses</th>
                    <th>Draws</th>
                </tr>

                <tr>
                    <td><span id="wins" name="wins">{{ games.wins }}</span></td>
                    <td><span id="losses" name="losses">{{ games.losses }}</span></td>
                    <td><span id="draws" name="draws">{{ games.draws }}</span></td>
                </tr>
            </table>
        </div>
    </div>


{% endblock %}
```
This is almost the same code as from pp module 9 but with few changes. At line 6 we show the logged in user with **{{ user.username }}** template tag. At line 10 is the form that we will use to update scores. At line 16 is the money field **{{ games.money }}** and at lines 47,48,49 are the scores fields **{{ games.wins }}**, **{{ games.losses }}** and **{{ games.draws }}**. 
Save the file Ctrl + S and go to terminal.
Now let's fill the signup .html. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>notepad signup.html
```
And place this code inside:
```html
{% extends "base.html" %}

{% block javascript %}
  <script>
	let list = document.querySelectorAll("input");
	for (let i = 0; i < list, length; i++) {
		  list[i].classList.add('form-control');
	  }
  </script>
{% endblock %}

{% block content %}
  <div class="container">
      <div class="row form_row">
      <div class="col-md-3"></div>
      <div class="col-md-6">
        <h1>Sign Up</h1>

            <form class="" method="post">{% csrf_token %}
                <fieldset>
                    <legend>{{ title }}</legend>
                    {% for field in form %}
                        {% if field.errors %}
                            <div class="form-group">
                                <label>{{ field.label }}</label>
                                    {{ field }}
                                <span class="help-inline">
                                    {% for error in  field.errors %}{{ error }}{% endfor %}
                                </span>

                            </div>
                        {% else %}
                            <div class="form-group">
                                <label>{{ field.label }}</label>
                                {{ field }}
                                    {% if field.help_text %}
                                        <p class="help-inline"><small>{{ field.help_text|safe }}</small></p>
                                    {% endif %}

                            </div>
                        {% endif %}
                    {% endfor %}
                </fieldset>
                <div class="form-actions">
                    <button type="submit" class="btn btn-primary" >Submit</button>
                </div>
            </form>
          </div>
        </div>
  </div>

{% endblock %}
```
Lines 3 to 10 is small JavaScript code to add the bootstraps 'form-control' class to input fields. At line 22 we use for loop to iterate the form fields and to give them bootstrap look.

Save the file Ctrl + S and go to terminal to open the login .html. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>notepad signup.html
```
Now fill it with code:
```html
{% extends "base.html" %}

{% block javascript %}
  <script>
	  let list = document.querySelectorAll("input");
	  for (let i = 0; i < list.length; i++) {
		  list[i].classList.add('form-control');
	  }
  </script>
{% endblock %}

{% block content %}

  <div class="row form_row">

      <div class="col-md-3"></div>
      <div class="col-md-6">
        <h1>Log In</h1>
            <form class="form-horizontal" method="post">{% csrf_token %}
                <fieldset>
                    <legend>{{ title }}</legend>
                    {% for field in form %}
                        {% if field.errors %}
                            <div class="form-group">
                                <label>{{ field.label }}</label>
                                {{ field }}
                                <span class="help-inline">
                                    {% for error in  field.errors %}{{ error }}{% endfor %}
                                </span>
                            </div>
                        {% else %}
                            <div class="form-group">
                                <label>{{ field.label }}</label>
                                {{ field }}
                                {% if field.help_text %}
                                    <p class="help-inline"><small>{{ field.help_text|safe }}</small></p>
                                {% endif %}
                            </div>
                        {% endif %}
                    {% endfor %}
                </fieldset>
                <div class="form-actions">
                    <button type="submit" class="btn btn-primary login" >Login</button>
                </div>
            </form>
     </div>
  </div>
{% endblock %}
```
As you can notice it is almost the same as signup html.
Save the file Ctrl + S and go to terminal. Now let's modify the css and js files.
* * *
#### 15. Editing css and js files
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>cd ..\..\..
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd static\game\css
(blackjackenv) C:\Users\Goran\blackjack_project\game\static\game\css>notepad style.css
```
Add the following lines at the bottom of the css file:
```css
.btn-lg {
	width: 100px;
}

/* Navbar */
ul.nav li {
    padding-left: 12px;
    text-transform: uppercase;
}

.control-label {
    font-weight: bold;
    padding-top: 5px;
}

.login {
    margin-top: 15px;
}

.form_row {
    margin-top:50px;
    background-color: rgba(10,10,10,0.4);
    padding-bottom: 30px;
    border-radius: 10px;
}

.btn-lg {
	width: 100px;
}

/* body and tbody */
body {
    background-image: url('http://www.africansunhotels.com/data/media/00000051/blackjack.jpg');
    background-size: cover;
    color: white;
    }

tbody {
    background-color: rgba(10,10,10,0.4);
}
```
Now the css file should look like this:
```css
.flex-box-container-1, .flex-box-container-2, .flex-box-rps, .flex-box-pick-color, .flex-blackjack-row-1, 
.flex-blackjack-row-2, 
.flex-blackjack-row-3, 
.flex-ajax-row-1 {
  display: flex;
  padding: 10px;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: space-around;
  border: 1px solid black;
}

.flex-box-container-1 div {
  display: flex;
  align-items: center;
}

.flex-box-container-2 div {
  display: flex;
  padding: 10px;
}

.cat-image {
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.7);
}

.flex-box-rps div {
  display: flex;
  justify-content: space-around;
  flex: 1;
}

.flex-box-rps img:hover{
  box-shadow: 0px 10px 50px rgba(37, 50, 233, 1);
}

.flex-blackjack-row-1, .flex-blackjack-row-2 {
  background: url('https://ie2-gfebf.cdnppb.net/mexchangeblackjack/turbo/17/assets/gameView/tableBackground.png?v17') center;
  color: #ffffff;
}

.flex-blackjack-row-1 div {
  border: 1px solid black;
  padding: 10px;
  flex: 1;
  text-align: center;
  height: 350px;
}

.flex-blackjack-row-1 img {
  width: 25%;
  padding: 10px;
}

.flex-blackjack-row-2 button {
  border: 1px solid black;
  padding: 10px;
}

.flex-blackjack-row-2 div {
  border: 1px solid black;
  padding: 10px;
}

table, th, td {
  padding: 5px;
  border: 1px solid black;
}

.container-1, .container-2, .container-3, .container-4, .container-5, .container-6 {
  border: 1px solid black;
  width: 75%;
  margin: 0 auto;
  text-align: center;
}

.flex-ajax-row-1 img {
  display: flex;
  align-items: center;
  padding: 30px;
}

/* Navbar */
ul.nav li {
    padding-left: 12px;
    text-transform: uppercase;
}

.control-label {
    font-weight: bold;
    padding-top: 5px;
}

.login {
    margin-top: 15px;
}

.form_row {
    margin-top:50px;
    background-color: rgba(10,10,10,0.4);
    padding-bottom: 30px;
    border-radius: 10px;
}

.btn-lg {
	width: 100px;
}

/* Navbar */
ul.nav li {
    padding-left: 12px;
    text-transform: uppercase;
}

.control-label {
    font-weight: bold;
    padding-top: 5px;
}

.login {
    margin-top: 15px;
}

.form_row {
    margin-top:50px;
    background-color: rgba(10,10,10,0.4);
    padding-bottom: 30px;
    border-radius: 10px;
}

.btn-lg {
	width: 100px;
}

/* body and tbody */
body {
    background-image: url('http://www.africansunhotels.com/data/media/00000051/blackjack.jpg');
    background-size: cover;
    color: white;
    }

tbody {
    background-color: rgba(10,10,10,0.4);
}
```
Save the file Ctrl + S and go to terminal to edit the JavaScript code. Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\static\game\css>cd..
(blackjackenv) C:\Users\Goran\blackjack_project\game\static\game>cd js
(blackjackenv) C:\Users\Goran\blackjack_project\game\static\game\js>notepad script.js
```
Replace the existing code with the code bellow:
```js
// Challenge 5: Blackjack
let blackjackGame = {
  'you': {'scoreSpan': '#your-blackjack-score', 'div': '#your-box', 'score': 0},
  'dealer': {'scoreSpan': '#dealer-blackjack-score', 'div': '#dealer-box', 'score': 0},
  'isStand': false,
  'turnsOver': false,
  // Here the values are the database values.
  'money': parseInt(document.querySelector('#money').textContent),
  'wins': parseInt(document.querySelector('#wins').textContent),
  'losses': parseInt(document.querySelector('#losses').textContent),
  'draws': parseInt(document.querySelector('#draws').textContent),
  'cardsMap': {'2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9, '10': 10, 'K': 10, 'Q': 10, 'J': 10, 'A': [1, 11]},
  'cards': ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'K', 'J', 'Q', 'A']
};

const YOU = blackjackGame['you'];
const DEALER = blackjackGame['dealer'];

// we are gonna use event listeners
document.querySelector('#blackjack-hit-button').addEventListener('click', blackjackHit);

document.querySelector('#blackjack-stand-button').addEventListener('click', dealerLogic);

document.querySelector('#blackjack-deal-button').addEventListener('click', blackjackDeal);

const hitSound = new Audio("/static/game/sounds/swish.m4a");
const winSound = new Audio("/static/game/sounds/cash.mp3");
const lossSound = new Audio("/static/game/sounds/aww.mp3");

function blackjackHit() {
  if (blackjackGame['isStand'] === false) {
    let card = randomCard();
	showCard(card, YOU);
    updateScore(card, YOU);
    showScore(YOU);
  }
}

function randomCard() {
  let randomIndex = Math.floor(Math.random() * 13);
  return blackjackGame['cards'][randomIndex];
}

function updateScore(card, activePlayer) {
  if (card === 'A') {
    if (activePlayer['score'] + blackjackGame['cardsMap'][card][1] <= 21) {
      activePlayer['score'] += blackjackGame['cardsMap'][card][1];
    } else {
      activePlayer['score'] += blackjackGame['cardsMap'][card][0];
    }
  } else {
    activePlayer['score'] += blackjackGame['cardsMap'][card];
  }
}

function showCard(card, activePlayer) {
  if (activePlayer['score'] <= 21) {
    let cardImage = document.createElement('IMG');
    cardImage.src = `/static/game/images/${card}.png`
    document.querySelector(activePlayer['div']).appendChild(cardImage);
    hitSound.play();
  }
}

function showScore(activePlayer) {
  if (activePlayer['score'] > 21) {
    document.querySelector(activePlayer['scoreSpan']).textContent = "BUST!";
    document.querySelector(activePlayer['scoreSpan']).style.color = 'red';
  } else {
    document.querySelector(activePlayer['scoreSpan']).textContent = activePlayer['score'];
  }
}

function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function dealerLogic() {
  blackjackGame['isStand'] = true;
  while (DEALER['score'] < 16 && blackjackGame['isStand'] === true) {
    let card = randomCard();
    showCard(card, DEALER);
    updateScore(card, DEALER);
    showScore(DEALER);
    await sleep(1000);
  }

  blackjackGame['turnsOver'] = true;
  showResult();
}

function blackjackDeal() {
  if (blackjackGame['turnsOver'] === true) {

    blackjackGame['isStand'] = false;

    let yourImages = document.querySelector('#your-box').querySelectorAll('img');
    let dealerImages = document.querySelector('#dealer-box').querySelectorAll('img');
    for (i=0; i<yourImages.length; i++) {
      yourImages[i].remove();
    }

    for (i=0; i<dealerImages.length; i++) {
      dealerImages[i].remove();
    }

    YOU['score'] = 0;
    DEALER['score'] = 0;

    document.querySelector('#your-blackjack-score').textContent = 0;
    document.querySelector('#dealer-blackjack-score').textContent = 0;

    document.querySelector('#your-blackjack-score').style.color = '#ffffff';
    document.querySelector('#dealer-blackjack-score').style.color = '#ffffff';

    document.querySelector('#blackjack-result').textContent = "Let's play";
    document.querySelector('#blackjack-result').style.color = 'black';

    blackjackGame['turnsOver'] = false;
    updateScoreDb();
  }
}

let twins = document.querySelector('#twins');
let tlosses = document.querySelector('#tlosses');
let tdraws = document.querySelector('#tdraws');

// show result on the top and update the score in the table
function showResult() {
  let message, messageColor;


  if (blackjackGame['turnsOver'] === true) {

    if (YOU['score'] <= 21) {

      // condition: higher score than dealer's or when dealer busts but you're 21 or under.
      if (YOU['score'] > DEALER['score'] || (DEALER['score'] > 21)) {
        blackjackGame['wins']++;
        blackjackGame['money'] += 10;
        document.querySelector('#wins').textContent =  blackjackGame['wins'];
        document.querySelector('#money').textContent =  blackjackGame['money'];
        message = 'You won!';
        messageColor = 'green';
        winSound.play();

      } else if (YOU['score'] < DEALER['score']) {
        blackjackGame['losses']++;
        document.querySelector('#losses').textContent =  blackjackGame['losses'];
        if (blackjackGame['money'] >= 10){
            blackjackGame['money'] -= 10;
        }
        document.querySelector('#money').textContent =  blackjackGame['money'];
        message = 'You lost!';
        messageColor = 'red';
        lossSound.play();

      } else if (YOU['score'] === DEALER['score']) {
        blackjackGame['draws']++;
        document.querySelector('#draws').textContent = blackjackGame['draws']; 
        message = 'You drew!';
        messageColor = 'black';
      }

      // condition: user busts but dealer doesn't
    } else if (YOU['score'] > 21 && DEALER['score'] <= 21) {
      blackjackGame['losses']++;
      document.querySelector('#losses').textContent = blackjackGame['losses'];
      if (blackjackGame['money'] >= 10){
            blackjackGame['money'] -= 10;
        }
      document.querySelector('#money').textContent =  blackjackGame['money'];
      message = 'You lost!';
      messageColor = 'red';
      lossSound.play();

    // condition: when DEALER bust.
    } else if (YOU['score'] > 21 && DEALER['score'] > 21) {
      blackjackGame['draws']++;
      document.querySelector('#draws').textContent = blackjackGame['draws'];
      message = 'You drew!';
      messageColor = 'black';
    }
  }

  document.querySelector('#blackjack-result').textContent = message;
  document.querySelector('#blackjack-result').style.color = messageColor;
  // If deal is not clicked this function will be triggered after 5 seconds.
  setTimeout(function(){

        updateScoreDb();

    },5000);
}

// Function to update the database
function updateScoreDb() {
    document.querySelector("#id_money").value = blackjackGame['money'];
    document.querySelector("#id_wins").value = blackjackGame['wins'];
    document.querySelector("#id_losses").value = blackjackGame['losses'];
    document.querySelector("#id_draws").value = blackjackGame['draws'];
    setTimeout(function(){

        document.querySelector("#update_button").click();

    },1);
}
```
* * *
#### 16. Testing the unhidden form 
Save the file Ctrl + S and lets do some migrations and to test the form before we hide it.
Go back to terminal and type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\static\game\js>cd ..\..\..
```
Now run the following 3 commands in this order:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py migrate
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py makemigrations
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py migrate
```
Now run:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py runserver
```
If you get output like :
```
Performing system checks...

System check identified no issues (0 silenced).
July 25, 2018 - 12:28:33
Django version 2.0.7, using settings 'game.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
Go to your web browser and type [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
Click the Sign Up at top right and create a user. Then login and test the form how it works. You can add values manually or play the game to see how values are changing and updating to database. When you get bored go to next step to hide the form and we will complete the project.
* * *
#### 17. Hiding the form and the submit button
Go back to terminal and press Ctrl + C to stop the server. Now type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>cd blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>notepad forms.py
```
At the class GameUpdateForm replace the widgets with the following code:
```python
# Hiding the form fields 
widgets = {
            'user': forms.HiddenInput(),
            'money': forms.HiddenInput(),
            'wins': forms.HiddenInput(),
            'losses': forms.HiddenInput(),
            'draws': forms.HiddenInput(),
        }
```
Now your form .py should look like this:
```python
from .models import User, Game
from django.contrib.auth.forms import UserCreationForm
from django import forms

# Sign Up form
class UserCreateForm(UserCreationForm):
     
    class Meta:
        model = User
        fields = ('username','email','password1','password2',)


# Game update form
class GameUpdateForm(forms.ModelForm):
    class Meta:
        fields = ('user','money','wins','losses', 'draws')
        model = Game
        # Hiding the form fields 
        widgets = {
            'user': forms.HiddenInput(),
            'money': forms.HiddenInput(),
            'wins': forms.HiddenInput(),
            'losses': forms.HiddenInput(),
            'draws': forms.HiddenInput(),
        }
```
Save the file Ctrl + S, go to terminal and let's hide the submit button.
Type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack>cd templates\blackjack
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>notepad index.html
```
To button at line 13 add the attribute hidden="hidden" and it should look like this:
```html
<button type="submit" id="update_button" hidden="hidden">Submit</button>
```
Save the file Ctrl + S. Now run the server again to see if it is hidden:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game\blackjack\templates\blackjack>cd ..\..\..
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py runserver
```
Go to browser type [http://127.0.0.1:8000/](http://127.0.0.1:8000/) and test the app that you have just created. 
You can create now superuser to log in at admin page and to see the score fields of all users.
Go to terminal and press Ctrl + C to stop the server. Now type:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py createsuperuser
```
Enter the user details that you are asked for. Run the server again:
```
(blackjackenv) C:\Users\Goran\blackjack_project\game>python manage.py runserver
```
Now login to admin page  [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin) with superuser credentials to see the fields of users that you have created.
## Good luck!
