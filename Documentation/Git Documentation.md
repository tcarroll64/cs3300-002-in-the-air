# Git Documentation

### Table of Contents

[Introduction](#introduction)

[Interacting with the Repository](#interacting-with-the-repository)

&nbsp;&nbsp;[Getting the Repository onto Your Local Machine](#getting-the-repository-onto-your-local-machine)

&nbsp;&nbsp;[Updating the Repository](#updating-the-repository)

&nbsp;&nbsp;[Branches](#branches)

[Commits](#commits)

&nbsp;&nbsp;[Commit Messages](#commit-messages)

&nbsp;&nbsp;[Viewing Previous Commits](#viewing-previous-commits)

[Tags](#tags)

&nbsp;&nbsp;[Viewing Previous Tags](#viewing-previous-tags)

[Merging](#merging)

[Extra Git Commands](#extra-git-commands)

[Additional Resources](#additional-resources)

### Introduction

This document serves as a one stop shop for the Git commands we will be using throughout this course. As we learn new concepts or techniques this document will get updated with information the tech lead or other group members find helpful for the group's success. As a note, all of the Git commands found in the document should be executed in the command line, personally I use [Git Bash](https://git-scm.com/downloads) but use whatever you are comfortable with. If you are looking for any specific information, click on the sections in the table of contents to find the information effeciently. If you want to have anything added to the document get with the current Git tech lead and let them know!

### Interacting with the Repository

This section will describe how to interact with the repository and actions you should take when you want to make changes. As a note, to be sure you are always working with the updated version of your repository you can check by using the `git status` command. If your session is out of date, to get the current version us the command below.

```bash
git pull
```

#### Getting the Repository onto Your Local Machine

This section will walk you through how to get the remote repository onto your local machine so you can start interacting with it.

1. Using the command line and package manager of your choice, install Git if it is not already installed
   
   ```bash
   apt install git
   ```

2. Find the [repository URL](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-URL-find-use-example) associated with your repository and copy it to your clipboard

3. Use the `git clone` command with your repository URL
   
   ```bash
   git clone <repository_url>
   ```
   
   If you would like to clone the repository into a specific directory, you can add the directory location after the repositroy URL as seen in the command seen below.
   
   ```bash
   git clone <repository_url> <local_directory_name>
   ```

4. You will most likely be on the `main` branch after cloning the repository. See [Branches](#branches) if you want to learn how to switch branches.

#### Updating the Repository

Whenever you want to send any changes you made on your local repository to the remote one, you must follow the steps of

1. Add

2. Commit

3. Push

Without doing these steps you will not be able to update the repository.

- Add - When you use `git add` you are essentially putting a file you modified into the staging area to be sent to your remote repository.
  
  ```bash
  git add .
  ```
  
  Using the `git add .` command will put any files from your working directory that are different from your remote repository into the staging area. This may not always be the best option if you do not want *every* modified file to be sent to your repository. If this is the case, you should instead add the specific file instead using the command seen below.
  
  ```bash
  git add <file_name>
  ```
  
  If you want to *interactively* choose which changes you want to put in the staging area you can use the command seen below. After issuing the command you will be prompted of the files that are different and whether or not you want them to be placed in the staging area to be commited and pushed to your remote repository.
  
  ```bash
  git add -i
  ```

- Commit - After staging your modified files, use `git commit` to mark why you made the changes. Every commit should have a unique messaged attatched about what was changed so that others (or yourself) know what was updated in the file.
  
  ```bash
  git commit -m "Reason for change"
  ```
  
  As seen above, the `-m` option lets you add a message with your commit to let others know why you updated a file on the repository
  
  As a shortcut method to combine `git add` and `git commit`, you can use the `-a` option that automatically stages any locally modified or deleted files before committing. As a note, using this option, every modified file will have the commit message you use.
  
  ```bash
  git commit -a -m "Reason for changes"
  ```
  
  **OR**
  
  ```bash
  git commit -am "Reason for changes"
  ```

- Push - To actually send your changes to the remote repository, you mush `push` your changes!
  
  ```bash
  git push
  ```
  
  As a note, if you just use the `git push` command without any additional arguments, Git will push your current branch to its corresponding branch on the remote repository that it is tracking. To push to a specific branch you can use the command seen below.
  
  ```bash
  git push origin <local_branch>:<remote_branch>
  ```

#### Branches

A repository will have various branches used for different things. As an example, when working on an applicaiton the code being used for the production version of the application will probably be in main and other branches could be experimental or testing versions of the application.

- Get a **list of all local branches attatched to your local repository and show the current branch** you are working on
  
  ```bash
  git branch
  ```

- To **change branches**
  
  ```bash
  git switch <branch_name>
  ```

- **An alternative way to change branches**
  
  ```bash
  git checkout <branch_name>
  ```
  
  If your only intention is to switch branches, you should use `git switch` instead since `git checkout` carries a greater risk of creating a new branch
  or performing unintended actions. 
  
  - `git checkout` can also be used to create a new local branch and switch to it as your current branch
    
    ```bash
    git checkout -b <new_branch_name>
    ```
  
  - `git checkout` can also be used to look at specific commits or tags (see [Viewing Previous Commits](#viewing-previous-commits) to find a commit's hash)
    
    ```bash
    git checkout <commit_hash_OR_tag_name>
    ```

- To **pull from a specific branch**
  
  ```bash
  git pull origin <branch_name>
  ```

- To **push to a specfic branch**
  
  ```bash
  git push origin <branch_name>
  ```

### Commits

A commit in Git is essentially like a 'snapshot' of your code at a given time. Commits allow for your changes to be easily tracked and refered to within a repository. When viewing commits via the GitHub website or when using the `git log` command, they show the commit's hash, author, timestamp, commit message and changes. 

#### Commit Messages

Every commit should have a message attatched specifying what was changed. When creating a commit message you should keep it **clear**, **concise**, and **informative** to avoid confusion on why you pushed a change to the repository! An example of a commit command and message can be seen below

```bash
git commit -m "Resolved bug when processing the customers info"
```

#### Viewing Previous Commits

At times you may be curious about previous commits to the repository and that is where the `git log` command comes into play. Every commit has information attatched to it which includes the commit's hash, author, timestamp, commit message and changes. The *commit's hash* (long hexadecimal string) can be used with various commands to learn more about what was changed in a commit.

- To see all commits to the repository and any extra information attatched to them
  
  ```bash
  git log
  ```
  
  - You can narrow down your search results by using the `--author="author_name"` option as well as the `--since="# days"` option
    
    ```bash
    git log --author="Joe Shmoe"
    ```
    
    ```bash
    git log --since="# days" 
    
    # can be more specific with time such as
    git log --since="YYYY-MM-DD" 
    
    # or even
    git log --since="3 days 10 hours ago" 
    ```

- To analyze a commit when you know the commit hash (ex. 411eb51cd4f28b5e3cc26f02f4f8fe8931435fd6)
  
  ```bash
  git show <commit_hash>
  ```

### Tags

Tags are used to label a version of your code. Tags can be helpful to refer to specific versions of your code or even identify who worked on an iteration of your program at a given time. **After creating a tag, you must push the tag to the remote repository!**

```bash
git tag <tag_name>
git push origin --tags    # Push tag to repo
```

#### Viewing Previous Tags

To see the tag attatched to a version you can use the `git show` command to see the tag of your current iteration or use the `git tag` command.

```bash
git show    # Will give a range of info including the tag
```

```bash
git tag    # Will show current tag
```

### Merging

In Git, merging is a way to combine changes from one branch into another branch. Merging can be helpful to clone a branch into another or even update your 'production' branch from a 'features' branch (as an example). Below are some general steps to follow when merging.

1. Make sure you are on the branch you want the changes to be applied to. As an example, if you want to merge your features branch **into** the main branch, you would want to be on the main branch
   
   ```bash
   git branch
   ```

2. Merge the two branches
   
   ```bash
   git merge <source_branch>    # Name of branch we want to merge into current branch
   ```

3. Resolve any merge conflicts
   
   1. Edit the code between `<<<<<<< HEAD` and `=========` to ensure the code is correct
   
   2. Save the files you resolved
   
   3. Add the resolved file to the staging area
      
      ```bash
      git add <resolved_file>
      ```
   
   4. Continue the merge
      
      ```bash
      git merge --continue
      ```

4. When the merge is complete, commit the merge with a message
   
   ```bash
   git commit -m "merged features branch into main branch"
   ```

5. Push the merged changes
   
   ```bash
   git push
   ```

### Extra Git Commands

This section will present some git commands that will be used and useful options that they have.

- ```bash
  git status
  ```
  
  Shows the status of your working directory and staged changes.

- ```bash
  git log
  ```
  
  Displays a chronological history of commits in a Git repository (press `q` to return to the terminal).

- ```bash
  git rm <file_name>
  ```
  
  Removes the file from your local system. If you want to remove it from the remote repository as well just make sure to commit + push your changes.

- ```bash
  git reset HEAD^
  ```
  
  Undos the <u>last commit</u> and unstages the changes to the branch. This can be helpful if you make a mistake (poor description/spelling mistake) when commiting.
  
  - Instead of 'Head^' can use the commit hash to select a specific staged commit to remove. See [Viewing Previous Commits](#viewing-previous-commits) for more information on commit hashes.

### Additional Resources

- [Git - Reference](https://git-scm.com/docs)
