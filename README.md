# MySocial App 
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
