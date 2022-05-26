# github-tips
Github commands to remember.

## Create a new repository on command line
  
```echo "# python-tips" >> README.md
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/ninyancat13/python-tips.git
git push -u origin master
```

## Push an existing repository from the command line
  
```git remote add origin https://github.com/ninyancat13/python-tips.git
git push -u origin master
```
## Line breaks in a md file
https://gist.github.com/shaunlebron/746476e6e7a4d698b373 . 

## Delete a file in a repository:
https://github.community/t5/How-to-use-Git-and-GitHub/How-to-delete-multiples-files-in-Github/td-p/4623  

In the command-line, navigate to your local repository.  
Ensure you are in the default branch:  
```git checkout master```  
The rm -r command will recursively remove your folder:  
```git rm -r folder-name```  
Commit the change:  
```git commit -m "Remove file in the repository"```  
Push the change to your remote repository:  
```git push origin master```  

## 
