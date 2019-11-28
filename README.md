# github-tips
Github commands to remember.

## Delete a file in a repository:
https://github.community/t5/How-to-use-Git-and-GitHub/How-to-delete-multiples-files-in-Github/td-p/4623

```In the command-line, navigate to your local repository.
Ensure you are in the default branch:
<b>git checkout master</b>
The rm -r command will recursively remove your folder:
<b>git rm -r folder-name</b>
Commit the change:
<b>git commit -m "Remove file in the repository"</b>
Push the change to your remote repository:
<b>git push origin master</b> 
```

## Create a new repository on command line:
<Credit goes to: github.com>
```echo "# python-tips" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/ninyancat13/python-tips.git
git push -u origin master
```

## Push an existing repository from the command line
<Credit goes to: github.com>
```git remote add origin https://github.com/ninyancat13/python-tips.git
git push -u origin master
```
