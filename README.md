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












