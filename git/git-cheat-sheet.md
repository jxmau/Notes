<h2> Save and Push to remote repo <h2>

```bash

> git status # Will show you the list of files who had changed and the files that wasn't added.

> git add [file relative path] # Will add a specific file to commit
> git add . # Will add every files listed on the git status

> git commit [file path or '.'] -m "Your message here" 

> git push # Will push the change to the git branch.

```

<h3> Git add  </h3>

```bash

git add . # Add all modified files, new files, and deleted files.

git add -A # Add only modified files.

git add -u # add modified and deleted files.

```