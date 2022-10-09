# MySocial App 
A social media application using Django Python Web Framework.<br/> <hr>
[Method to fully push Vscode project to Github](https://stackoverflow.com/questions/46877667/how-to-add-a-new-project-to-github-using-vs-code):<br/>
Create a new repo on Github profile, copy the newly generated `.git` link. <br/>
In Vscode project, open the Terminal: <br/> 
`git init`<br/> 
`git commit -m "COMMIT MESSAGE"`<br/> 
`git remote add origin .GIT LINK OBTAINED FROM ABOVE`<br/> 
`git push -u origin master`<br/>
Then in Settings-> Enable Git<br/>
Source Control -> right click 3 dots -> Create new Branch -> name new branch -> Publish Branch <br/>
Refresh the repo link on webpage, the entire project is pushed. <br/> 
# Functionalities/Demo:
- Users will be able to post feeds(upload pictures, texts) on their profiles.
- Feature that allows users to like and unlike other users’ posts.
- Being redirected to their profiles once clicking their usernames.
- Displaying the amount of following and followers on users’ profiles.
- Enabling users to follow and unfollow other users.
- Providing following suggestions on the Home page sidebar.
- Account Setting feature to change profile image, bio and location.
- Search bar to search for specific usernames.
- Login section with authentication after logout.
# Developing tools:
[Django 4.1](https://www.djangoproject.com)<br/>
[MacBook OS Monterey Version 12.6](https://www.apple.com/macos/monterey/)<br/>
[Python 3.10.7](https://www.python.org/downloads/)<br/>
[Anaconda Python Environment 3.9](https://www.anaconda.com/products/distribution)<br/>
# Build
[Prerequisites & Setup](https://github.com/KrystalZhang612/MySocial-App/blob/main/README.md#prerequisites--setup)<br/>
[Method Running The Project(Locally)](https://github.com/KrystalZhang612/MySocial-App/blob/main/README.md#method-running-the-projectlocally)<br/>
[Debugging&Troubleshooting](https://github.com/KrystalZhang612/MySocial-App/blob/main/README.md#debuggingtroubleshooting)<br/> 
[Synchronous Developing Notes](https://github.com/KrystalZhang612/MySocial-App/blob/main/README.md#synchronous-developing-notes)<br/> 
[Testing Results](https://github.com/KrystalZhang612/MySocial-App/blob/main/README.md#testing-results)<br/> 

# Prerequisites & Setup:
Create a new folder named `my_social_app`. Obtain its local directory.<br/>
Install Django:<br/>
In Mac Terminal:<br/>
`cd <my_social_app DIRECTORY>`<br/>
`pip install django`<br/>
Create a new Django project in `my_social_app`:<br/>
`django-admin startproject my_social_app`<br/>
Locate to the new folder generated:<br/>
`cd my_social_app`<br/>
Create [Core](https://github.com/KrystalZhang612/MySocial-App/tree/main/core) app to handle various functionalities:<br/>
`django-admin startapp core`<br/>
Initial run to make sure the project works:<br/>
`python3 manage.py runserver`<br/>
If we get the following message, the project setup is done:<br/>
`System check identified no issues (0 silenced).`<br/>
`You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.`<br/>
`Django version 4.1.1, using settings 'my_social_app.settings' Starting development server at http://127.0.0.1:8000/`<br/>
`Quit the server with CONTROL-C.`<br/>
Where the url http://127.0.0.1:8000/ is our Localhost for future performance.<br/>
Open the Localhost, if we see:<br/>
`The install worked successfully! Congratulations!`<br/> 
 `You are seeing this page because DEBUG=True is in your settings file and you have not configure any urls. `<br/> 
Then all setups are done.<br/> 
# Method Running The Project(Locally) 
Download the entire `my_social_app` project to local directory<br/>
On local device Terminal, use `cd` to locate to the project to `...my_social_app/my_social_app`<br/>
For Windows user: Run `python manage.py runserver` and open Localhost at http://127.0.0.1:8000/ to test the App. <br/>
For macOS user: Run `python3 manage.py runserver` and open Localhost at http://127.0.0.1:8000/ to test the App. <br/> 
`CONTROL+C` to terminate testing. <br/> 
# Debugging&Troubleshooting
- Temporary Error:  `raise ValueError(ValueError: The view core.views.signup didn't return an HttpResponse object. It returned None instead.
"POST /signup HTTP/1.1" 500 61151`. DEBUGGING: In views.py, import messages and authentication of user model: `from django.contrib.auth.models import User, auth  from django.contrib import messages` Then in Terminal: `format document->CONTROL+C-> python3 manage.py runserver`.
- Noticeable Error: 10k+ tracking forks on the sidebar Source Control every time press CONTROL+C to re-run the localhost server, unable to remove the accidentally fetched `.gitignore.`. DEBUGGING: METHOD 1: Right-click main in Source Control and select Close Repositories. DO NOT use python shell virtual environment in Terminal, if activated by accident, deactivate virtualenv with: `conda deactivate`. METHOD 2: Delete the entire .Git folder to temporarily disable Source Control: In Vscode: `Preference-> Settings-> Git Enabled(CLICK OFF)`. Now we successfully disable SCM from auto-fetching the .GIt root repositories.
- ERROR: Django return "Profile matching query does not exist" when refresh Account Setting page. DEBUGGING: Request new url link for Profile Image-> profileimg in setting.html: `<div class="col-span-2"> <label for=""> Profile Image</label> class="shadow-none bg-gray-100"> <img width="100" height="100" src="{{user_profile.profileimg.url}}" /> <input type="file" name="image" value="" </div>`. 
- 









# Synchronous Developing Notes
## ***URL Routing:***
Import and open the project with Visual Studio Code IDE.<br/>
Create a new file named urls.py under Core.<br/> 
In [urls.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/urls.py):<br/>
```python
from django.urls import path
  urlpatterns = [
    path('', views.index, name = “index”)]
```
use views.index to access views.py here.<br/> 
Create a simple HTTP Response request in [views.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/views.py):<br/>
```python 
from django.http import HttpResponse
```
Import views: 
```python
from . import views
```
To get urls reflected on the main, under my_social_app folder<br/>
modify [urls.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/my_social_app/urls.py):
```python 
 from django.urls import path, include
 urlpatterns = [
    path("admin/", admin.site.urls),
    path('', include('core.urls'))]
```
Refresh localhost http://127.0.0.1:8000:<br/>
[welcome testing white page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/welcome%20testing%20white%20page.png)<br/>
## ***Template Setup:***
Configurations setup:<br/>
in [settings.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/my_social_app/settings.py):
```python 
import os
```
Create a new folder named [templates](https://github.com/KrystalZhang612/MySocial-App/tree/main/templates) to hold all html files. Need to tell Django:
```python
 "DIRS": [os.path.join(BASE_DIR, "templates")]
```
Drag all html files (index.html, setting.html, signin.html, signup.html, profile.html) into templates.<br/>
In [views.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/views.py):
```python 
return render(request, "index.html")
```
Now all templates are cluttered on localhost:<br/>
[all templates are uploaded.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/all%20templates%20are%20uploaded.png)<br/>
## ***Static Files:***
Refresh Vscode IDE, create a new folder named [static](https://github.com/KrystalZhang612/MySocial-App/tree/main/static):<br/>
Set up static files roots in [settings.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/my_social_app/settings.py):
```python 
STATIC_URL = "static/"
STATIC_ROOT = os.path.join(BASE_DIR, "staticfiles")
STATICFILES_DIRS = (os.path.join(BASE_DIR, "static"), )
```
Move and copy all static files into the static folder.<br/>
Now in [index.html](https://github.com/KrystalZhang612/MySocial-App/blob/main/templates/index.html), we have all static properties loaded:
```JavaScript 
    <link rel="stylesheet" href="{% static 'assets/css/icons.css' %}">
    <link rel="stylesheet" href="{% static 'assets/css/uikit.css' %}">
    <link rel="stylesheet" href="{% static 'assets/css/style.css' %}">
    <link rel="stylesheet" href="{% static 'assets/css/tailwind.css'%}">
```
Change the configuration of the JavaScript link to the favicon.PNG image:
```JavaScript
<link href="{% static 'favicon.png' %}" rel="icon" type="image/png">
```
Refresh the localhost, we get [basic all JavaScript worked template.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/basic%20all%20JavaScript%20worked%20template.png)<br/>
## ***Creating a Profile Model:***
Create authentication with the website->Register and login to the social media:<br/>
we need to create a customized profile model, so in [models.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/models.py), extend database, create a separate model to the profile and link it to the user model using [foreign key](https://en.wikipedia.org/wiki/Foreign_key). <br/>
import contrib.auth to get user model and initialize it:<br/>
```python 
from django.contrib.auth import get_user_model
User = get_user_model()
```
Create all necessary attributes to specify profile model:
```python 
 class Profile(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    id_user = models.IntegerField()
    bio = models.TextField(blank=True)
    profileimg = models.ImageField(upload_to='profile_images',
default='blank-profile-picture.png')
    location = models.CharField(max_length=100, blank=True)
```
Here, create a new [media](https://github.com/KrystalZhang612/MySocial-App/tree/main/media) folder to hold the default avatar, which is:
[blank-profile-picture.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/media/blank-profile-picture.png) here. <br/>
Configure media url and root in [settings.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/my_social_app/settings.py):
```python
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```
Also configure the url pattern in [urls.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/urls.py):
```python 
urlpatterns = urlpatterns+static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```
Now return the username:
```python 
def __str__(self):
        return self.user.username
```
Open the Terminal panel:<br/> 
Now we got the following admin access for the static files:<br/>
```JavaScript 
"GET /static/admin/css/fonts.css HTTP/1.1" 304 0
"GET /static/admin/fonts/Roboto-Regular-webfont.woff HTTP/1.1" 304 0 
"GET /static/admin/fonts/Roboto-Light-webfont.woff HTTP/1.1" 304 0 
"GET /static/admin/fonts/Roboto-Bold-webfont.woff HTTP/1.1" 304 0
```
Now we need to make migrations:<br/>
`python3 manage.py makemigrations`<br/>
Migrations for core app are made:<br/>
`Migrations for 'core':`<br/> 
  `core/migrations/0001_initial.py`<br/> 
    `- Create model Profile`<br/>
Now migrate:<br/> 
 `python3 manage.py migrate`<br/>
The migrations operations are all successful:<br/>
```JavaScript 
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, core, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying core.0001_initial... OK
  Applying sessions.0001_initial... OK
```
As admin, we need to create a super user, which is the administrator as ourselves:<br/>
`python3 manage.py createsuperuser`<br/>
Create username, email address and password for admin login.<br/>
Then to make the profile models visible on `admin` portal, in [admin.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/admin.py):
```python 
from .models import Profile admin.site.register(Profile)
```
Now open and login to http://127.0.0.1:8000/admin/ , we have:<br/> 
[admin portal initial view.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/admin%20portal%20initial%20view.png)<br/> 
## ***Signup:***
Add a new signup path in [urls.py(Core)](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/urls.py):
```python 
path('signup', views.signup, name = 'signup' )
```
Create the signup view in [views.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/views.py):
```python 
def signup(request):
    return render(request, "signup.html")
```
Type http://127.0.0.1:8000/signup we got: [signup initial page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/signup%20initial%20page.png)<br/>
Since passwords are confidential values, we need to use POST method in [signup.html](https://github.com/KrystalZhang612/MySocial-App/blob/main/templates/signup.html):
```JavaScript
<form action= "" method = "POST">
```
Also we use a CSRF token to prevent CSRF attacks:
```JavaScript 
{% csrf_token %}
```
## ***Implement the Signup View:***
If use POST method, load all user attributes:
```python 
 def signup(request):
     if request.method == "POST":
        username = request.POST['username']
        email = request.POST['email']
        password = request.POST['password']
        password2 = request.POST['password2']
```
If two passwords matched and input email exists, redirect user back to signup page:
```python 
 if password == password2:
            if User.objects.filter(email=email).exists():
                messages.info(request, 'Email Taken')
                return redirect('signup')
```
If two passwords matched and input username exists, redirect back to signup page:
```python
 elif User.objects.filter(username=username).exists():
                messages.info(request, 'Username Taken')
                return redirect('signup')
```
If two passwords matched and new user, create a new user with all the infos and save:
```python 
 else: user = User.objects.create_user(username=username,email=email, password=password)
 user.save()
```
Render the request:
```python 
return render(request, "signup.html")
```
Now in [signup.html](https://github.com/KrystalZhang612/MySocial-App/blob/main/templates/signup.html), create styles to highlight red the duplicate warning message:
```JavaScript 
 <div> <style>
           h5 {color: red; }
</style>
                {% for message in messages %}
             <h5>{{message}}</h5>
                 {% endfor %}  </div>
```
Now test the signup page with existing username, email and unmatched PWs should get:<br/>
[user taken.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/user%20taken.png)<br/> 
[email taken.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/email%20taken%20.png)<br/> 
[unmatched passwords.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/unmatched%20passwords.png)<br/>
Now with no error, we want the system to automatically create a new user with creating a new profile that we can view in our `Django Administration` page. So in [views.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/views.py):
```python 
#log user in and redirect them to settings page
 #create a Profile object for the new user
      user_model = User.objects.get(username=username)
      new_profile = Profile.objects.create(user=user_model,
id_user=user.id)
      new_profile.save()
      return redirect('signup')
```
Also import Profile Model to make profile creation work:
```python 
from .models import Profile
```
Now register new user on Signup portal, and refresh from the admin portal, we can see that the user we just registered has their username and profile successfully created: <br/>
[user's username and their profile created.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/user's%20username%20and%20their%20profile%20created.png)<br/>
## ***Signin and Logout:***
Add a new path in [urls.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/urls.py):
```python 
path('signin', views.signin, name = 'signin' )
```
In [views.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/views.py), create a new sign in request:
```python 
def signin(request):
    return render(request, "signin.html")
```
type in http://127.0.0.1:8000/signin we get:<br/>
[signin page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/signin%20page.png)<br/>
Configure POST Method for login authentication:<br/>
In views.py, if user exists after input username and password, log the user in, if the user does not exist or either password OR username is incorrect, “credential invalid”:<br/>
```python 
 def signin(request):
        if request.method == "POST":
        username = request.POST['username']
        password = request.POST['password’]
        user = auth.authenticate(username=username, password =
password)
        if user is not None:
            auth.login(request, user)
            return redirect('/')
        else:
            messages.info(request, 'Credentials Invalid')
            return redirect('signin')
        else:
        return render(request, "signin.html")
```
[Credential invalid message.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/credential%20invalid%20message.png)<br/>
To achieve logout, start by creating a new logout path in [urls.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/urls.py):
```python 
path('logout', views.logout, name = 'logout' ),
```
Then define Logout functionality in [views.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/views.py):
```python
def logout(request):
    auth.logout(request)
    return redirect('signin')
```
Now if the user click the sidebar logout, they will be redirected to sign in page.<br/>
Also we need to import login_required:
```python 
from django.contrib.auth.decorators import login_required
```
which for security purposes will redirect the user to the login page if detected user not logged in. Along with the signature above index request:
```python 
 @login_required(login_url='signin')
```
So that when we refresh the home page, sign in page will show with the following url:<br/>
[redirect to signin url.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/redirect%20to%20signin%20url.png)<br/>
http://127.0.0.1:8000/signin?next=/ <br/> 
So if ONLY the registered user sign in here they will be redirected to the home page.<br/>
## ***Account Settings:***
Start by creating a new Settings path in [urls.py](https://github.com/KrystalZhang612/MySocial-App/blob/main/core/urls.py):
```python 
path('settings', views.settings, name = 'settings'),
```
Also render the request from setting.html in views.py:
```python
@login_required(login_url='signin')
def settings(request):
    return render(request, "setting.html")
```
Now if we type in http://127.0.0.1:8000/settings <br/> 
Account Settings page should appear available for user to edit Basic and Privacy Infos:<br/>
[Account Setting initial page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/Account%20setting%20initial%20page.png)<br/> 
## ***Log the new registered user automatically to Account Setting page:***
```python 
   #log user in and redirect them to settings page
                user_login = auth.authenticate(username=username,
password=password)
                auth.login(request, user_login)
                #create a Profile object for the new user
                user_model = User.objects.get(username=username)
                new_profile = Profile.objects.create(user=user_model,
id_user=user.id)
                new_profile.save()
                return redirect('settings')
```
Now we want specific username to show up on Account Setting page:
In settings.html: 
```JavaScript 
<h1 class="text-2xl leading-none text-gray-900 tracking-tight mt-3"><a href="/">Home</a> / Account Setting for <b>{{user.username}}</b></h1>
```
[Home/ Account Setting for username.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/%20Home:%20Account%20Setting%20for%20username.png)<br/>
Remove Privacy, the overview of the General left only setting page:<br/>
[general left only account setting.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/general%20left%20only%20account%20setting.png)<br/>
Remove Working at and Relationship:<br/>
[simplified setting.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/simplified%20setting.png)<br/>
Give user option to upload profile image:
```JavaScript 
  <div class="col-span-2">
           <label for=""> Profile Image</label>
           <input type="file" name="image" placeholder=""
class="shadow-none bg-gray-100">
                    </div>
```
[profile image upload.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/profile%20image%20upload.png)<br/>
Now besides allowing user to upload their own profile image, the default avatar shows:<br/>




















# Testing Results
[welcome testing white page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/welcome%20testing%20white%20page.png)<br/>
[all templates are uploaded.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/all%20templates%20are%20uploaded.png)<br/>
[basic all JavaScript worked template.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/basic%20all%20JavaScript%20worked%20template.png)<br/>
[blank-profile-picture.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/media/blank-profile-picture.png)<br/>
[admin portal initial view.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/admin%20portal%20initial%20view.png)<br/> 
[signup initial page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/signup%20initial%20page.png)<br/>
[user taken.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/user%20taken.png)<br/> 
[email taken.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/email%20taken%20.png)<br/> 
[unmatched passwords.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/unmatched%20passwords.png)<br/>
[user's username and their profile created.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/user's%20username%20and%20their%20profile%20created.png)<br/>
[Credential invalid message.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/credential%20invalid%20message.png)<br/>
[redirect to signin url.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/redirect%20to%20signin%20url.png)<br/>
[Account Setting initial page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/Account%20setting%20initial%20page.png)<br/> 
[Home/ Account Setting for username.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/%20Home:%20Account%20Setting%20for%20username.png)<br/>
[general left only account setting.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/general%20left%20only%20account%20setting.png)<br/>
[simplified setting.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/simplified%20setting.png)<br/>
[profile image upload.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/profile%20image%20upload.png)<br/>






















