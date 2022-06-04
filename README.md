# git & github-tips
Git commands to remember.

## Create a new repository

### `Git clone`: starting afresh (the simplest way)
1. Create repository on github UI
2. Go to command line and type 
```
git clone <URL of repository>
```
Note:
- `git clone` is basically a combination of:
    - `git init` (create the local repository)
    - `git remote add` (add the URL to that repository)
    - `git fetch` (fetch all branches from that URL to your local repository)
    - `git checkout` (create all the files of the main branch in your working tree)

    Aka, it not only creates the remote repository but copies all of the remote files to your local too. 

### `Git init`: when your project already exists locally, but it doesn't have Git yet. 
`Git init` turns any directory into a Git repository.

- You still need to go into the Github UI to create a repository called 'new-repo' for this to work. However you could use something like a github command line interface to bypass this (see notes underneath). 

#### Create a new repository (with new readme.md file) and then push to Github
```
echo "# new-repo" >> README.md (OR 'touch README.md' works fine too)
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/ninyancat13/new-repo.git
git push -u origin main
```
*To be fairly honest, I don't really see the point of using `git init` like this when it is much easier to just use `git clone` if we are creating a new repository. Maybe I am wrong though...

#### If you already have the <b>repository</b>* on your local, but you want to push it to Git just use
```
git remote add origin https://github.com/ninyancat13/new-repo.git
git branch -M main
git push -u origin main
```
*I say repository here on purpose because it is not just a file with scripts. It is a repository (aka no need to run git init)


#### If you have the directory you want to convert to repository and put on Github, first go into the directory and then run:
```
git init
git add --all
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/ninyancat13/new-repo.git
git push -u origin main
```
*I created this one by myself using combination of the two above. I believe it should work. Will test it soon.

Note:
- Why use git init?
    - The main purpose of `git init` is for projects that already exist that need to be turned into a repository and saved to Github. Unlike the `git clone` command, you do not transfer remote files to local. Instead it is more likely you will use `git init` when you actually already had a project on local (whether it already be a local repo or just an ordinary file with scripts) and you then want to 'convert' it over to a remote Github repo to save. In most cases, you will probably use `git clone` method as it is easier to first create the repo on the UI and then clone it to remote, and then start a project.
    
- I want to do everything in the command line without touching Github?
    - Use Github Command Line Interface. This would allow you to go from start to finish without interacting with the Github UI in any way.
https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-locally-hosted-code-to-github?fbclid=IwAR1zg-NPyN05pl4N2Lvs_zjCl1UgiAL0D7Sve3YItNCyQW-d5f4uswM3dsU

- Touch vs Echo?
    - So with echo >> file , you get one byte written to the file. If the file already existed, then it would have one byte added to it, because you used >> (append) instead of > (overwrite). touch creates a file if it didn't already exist, and updates the timestamps on it otherwise.

- Why use something like 'git branch -M main'?
    - Spurred by the rise in racism cases across the US, GitHub recently renamed its 'master' branch to 'main'. 
    - -M is a flag (shortcut) for --move --force per the docs page on git branch. It renames the branch main (since the default branch name for repositories created using the command line is master, while those created in GitHub [starting in Oct. 2020] have a default name of main) and forces it (allows renaming of the branch even if the new branch name already exists). 

## Push an existing repository from the command line
  
```git remote add origin https://github.com/ninyancat13/python-tips.git
git push -u origin master
```

OR simply
```
git push
```

Note:
- Origin means the remote repository on Github itself.
- We use -u origin master because technically, the -u flag adds a tracking reference to the upstream server you are pushing to. What is important here is that this lets you do a git pull without supplying any more arguments. For example, once you do a git push -u origin master, you can later call git pull and git will know that you actually meant git pull origin master.

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

Another simpler way to branch
```
git switch -C bugfix
```
This one effectively creates a branch whilst also changing to the branch (checking it out) too.
 
Reference:
A mix of Stackoverflow and Git Guides 
https://github.com/git-guides
