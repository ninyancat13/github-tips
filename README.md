# github-tips
Github commands to remember. Can also visit Git Guides for more detailed information: 

## Create a new repository

### Git clone: starting afresh (the simplest way)
1. Create repository on github UI
2. Go to command line and type 
```
git clone <URL of repository>
```
Note:
- git clone is basically a combination of:
    - `git init` (create the local repository)
    - `git remote add` (add the URL to that repository)
    - `git fetch` (fetch all branches from that URL to your local repository)
    - `git checkout` (create all the files of the main branch in your working tree)

### Git init: when your project already exists locally, but it doesn't have Git yet. 
Git init turns any directory into a Git repository.
Note: 
- You still need to go into the Github UI to create a repository called 'new-repo' for this to work. However you could use something like a github command line interface to bypass this (see notes underneath). The main purpose of `git init` is for projects that already exist that need to be turned into a repository and saved to Github.

Create a new repository (with new readme.md file) and push to Github
```
echo "# new-repo" >> README.md (OR 'touch README.md' works fine too)
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/ninyancat13/new-repo.git
git push -u origin main
```

### If you already have the repository on your local, but you want to push to Git
```
git remote add origin https://github.com/ninyancat13/new-repo.git
git branch -M main
git push -u origin main
```

Note:
- I want to do everything in the command line without touching Github?
    - Use Github Command Line Interface. This would allow you to go from start to finish without interacting with the Github UI in any way.
https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-locally-hosted-code-to-github?fbclid=IwAR1zg-NPyN05pl4N2Lvs_zjCl1UgiAL0D7Sve3YItNCyQW-d5f4uswM3dsU

- Touch vs Echo?
    - So with echo >> file , you get one byte written to the file. If the file already existed, then it would have one byte added to it, because you used >> (append) instead of > (overwrite). touch creates a file if it didn't already exist, and updates the timestamps on it otherwise.

- Why use something like 'git branch -M main'?
    - -M is a flag (shortcut) for --move --force per the docs page on git branch. It renames the branch main (since the default branch name for repositories created using the command line is master, while those created in GitHub [starting in Oct. 2020] have a default name of main) and forces it (allows renaming of the branch even if the new branch name already exists).

## Push an existing repository from the command line
  
```git remote add origin https://github.com/ninyancat13/python-tips.git
git push -u origin master
```
OR simply
```
git push
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

## Branching example
```
git checkout master
git branch new-branch
git checkout new-branch
... create your code ... e.g. vim code.py
git add -A
git commit -m "initial commit"
git checkout master
git merge new-branch
git push
```
 
