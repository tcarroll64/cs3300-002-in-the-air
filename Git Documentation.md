# Git Documentation

### Table of Contents

1. [Introduction](#introduction)

2. [Interacting with the Repository](#interacting-with-the-repository)
   
   1. [Getting the Repository onto Your Local Machine](#getting-the-repository-onto-your-local-machine)
   
   2. [Updating the Repository](#updating-the-repository)
   
   3. [Branches](#branches)

3. [Commits](#commits)
   
   1. [Commit Messages](#commit-messages)
   
   2. [Viewing Previous Commits](#viewing-previous-commits)

4. [Tags](#tags)
   
   1. [When to Tag a Commit](#when-to-tag-a-commit)
   
   2. [Viewing Previous Tags](#viewing-previous-tags)

5. [Merging](#merging)

6. [Extra Git Commands](#extra-git-commands)

7. [Additional Resources](#additional-resources)

### Introduction

This document serves as a one stop shop for the Git commands we will be using throughout this course. As we learn new concepts or techniques this document will get updated with information the tech lead or other group members find helpful for the group's success. As a note, all of the Git commands found in the document should be executed in the command line, personally I use [Git Bash]([Git - Downloads](https://git-scm.com/downloads)) but use whatever you are comfortable with. If you are looking for any specific information, click on the sections in the table of contents to find the information effeciently. If you want to have anything added to the document get with the current Git tech lead and let them know!

### Interacting with the Repository

This section will describe how to interact with the repository and actions you should take when you want to make changes.

##### Getting the Repository onto Your Local Machine

This section will walk you through how to get the remote repository onto your local machine so you can start interacting with it.

1. Using the command line and package manager of your choice, install Git if it is not already installed
   
   ```bash
   apt install git
   ```

2. Find the [repository URL]([How to find and use a GitHub URL by example](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-URL-find-use-example)) associated with your repository and copy it to your clipboard

3. Use the `git clone` command with your repository URL
   
   ```bash
   git clone <repository_url>
   ```
   
   If you would like to clone the repository into a specific directory, you can add the directory location after the repositroy URL as seen in the command seen below.
   
   ```bash
   git clone <repository_url> <local_directory_name>
   ```

4. You will most likely be on the `main` branch after cloning the repository. See [Branches](#branches) if you want to learn how to switch branches.

##### Updating the Repository

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

##### Branches

### Commits

##### Commit Messages

##### Viewing Previous Commits

### Tags

##### When to Tag a Commit

##### Viewing Previous Tags

### Merging

### Extra Git Commands

This section will present some git commands that will be used and useful options that they have.

- ```bash
  git status
  ```
  
  Shows the status of your working directory and staged changes.

- ```bash
  git branch
  ```
  
  Lists all local branches and shows the current branch.

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


