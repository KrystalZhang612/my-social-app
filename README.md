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











# Testing Results
[welcome testing white page.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/welcome%20testing%20white%20page.png)<br/>
[all templates are uploaded.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/all%20templates%20are%20uploaded.png)<br/>
[basic all JavaScript worked template.PNG](https://github.com/KrystalZhang612/MySocial-App/blob/main/basic%20all%20JavaScript%20worked%20template.png)<br/>















