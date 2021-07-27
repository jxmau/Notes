<h1>How to link a remote repo to a github repo </h1>

In order to do this, you'll need to create the repo on Github first.

```bash

> git init # Create a git repo on your folder

> git add . # Will add everything, exepted what's blacklisted by the .gitignore.

> git commit . -m "init" # Commit everything that you've added.
                         # Commiting, will create the branch

> git branch -M main # Will rename your main branch. 

> git remote add origin [the git path] # Add the URl given by github.

> git push -u origin main # Will push the local repo to the git repo.


```