# Learn Git and Github

### What is diff and how to use it?
- diff is used to find the differences between two files.
- diff -u is used to compare two files, line by line, and have the differing lines compared side-by-side in the same output.
- for example, you have two files:
```hello.txt``` and ```hello_updated.txt```, and you want to find the difference between these two files then you can use:
``` diff -u hello.txt hello_updated.txt ```

### What is patch and how to use it?
- patch is used to apply the file differences.
- for example, you have two files named ```hello.txt``` and ```hello_updated.txt``` and you want the difference between these two files to be applied to ```hello.txt```, below are the steps to do this:
  - #### Step 1: Create the differing file
  ``` diff -u hello.txt hello_updated.txt > new_hello.diff ```
  This command will create the differing file with name ```new_hello.diff```
  - #### Step 2: Apply the differences to ```hello.txt``` file
  ``` patch hello.txt < new_hello.diff ```

### Installing Git
- How to check whether you've git installed or not?
``` git --version ```
- Installing git on Linux using package manager:
``` apt install git ``` or ``` yum install git ```
- Installing git on MacOS:
Run the command: ``` git --version ```
If git is not installed then this command will ask you to download and install git.

### First steps with Git
Before we start using Version Control System(VCS), we need to tell git who we are, so we can do this using the config command:
``` git config --global user.email 'name@example.com  ``` and then ``` git config --global user.name 'Your name' ```
The ``` --global ``` sets these values for all the git repositories, but we can also set different values for different repositories.

- ### Creating an empty git repository
``` git init ``` 
The git init will create an empty git repository.
- ### Adding the file
To make git to track our files we will add that file to our project:
``` git add file_name.txt ```
It will add the file to the staging area.
> Staging area or index is a file maintained by Git that contains all of the information about what files and changes are going to go into your next commit.

- ### Checking the status
``` git status ```
Using git status we can get the information about current working tree and the pending changes.

- ### Committing the files
To get the files in the staging area to be committed in the .git directory we use ``` git commit ``` command. It will open the default editor and ask for commit message. After writing the commit message, save the changes and you're done with your first commit.
If you don't want to open the editor for writing the commit message, then you can also commit using ``` -m ```:
``` git commit -m 'This is some commit message' ```

- ### Checking the history of commits
``` git log ```
It shows the list of commits in the current git repository.

### Advanced GIT Interaction

- ### Skipping the staging area
You can skip the staging area by using:
``` git commit -a -m 'commit message' ```
the  ``` -a ``` will add all the modified files and then commit. But one things needs to be noted is that ``` -a ``` will only add those files that are modified, it won't add the new files. 

- ### Getting more information about the changes made
  - ``` git log ``` shows the list of commits in the current git repository. By default it shows the Author, date, and the commit message. But if you want to check what changes are made in the files in that commit then you can use: ``` git log -p ```, the ``` -p ``` flag shows the changes made to the files in the commit with pluses and minuses. The 'p' in ``` -p ``` comes from the patch. And the output is same as ``` diff -u ``` command.
  - ``` git log -p ``` shows all the commits. But if you want to see the changes made to the specific commit then you can use: ``` git show commit_id ```. This flag will show the changes made to that specific commit. Here ``` commit_id ``` is the id of the commit for which you want to see the changes made.
  - ``` git log --stat ``` shows the stats about our commit such as how many files are changed and how many lines are added or removed.
  - ``` git diff ``` shows the changes made to the files, the output is same as the command ``` diff -u ```. But ``` git diff ``` only shows the changes that are unstaged. So, when you've staged your changes then ``` git diff ``` won't show anything. Now you have to use ``` git diff --staged ``` to see the changes made or staged changes.
  -  ``` git add -p ``` allows a user to interactively review patches to add to the current commit.

- ### Removing and renaming files
If you want to delete a file from your repository, you can use: ``` git rm file_name ```.
If you want to rename a file from your repository, you can use: ``` git mv file_name new_file_name ```

- ### Undoing Things
  - Let say you've a file named hello_world.txt and you've made some changes to it. Now it's modified. But now you want to revert the changes then you can do this using: ``` git checkout hello_world.txt```, using this command the file will come to its previous state that was in before making changes.
  - ``` git add * ``` will add all the files to the staging area.
  - To remove the files from the staging area you can use: ``` git reset HEAD hello_world.txt ```, think of reset HEAD as the opposite of git add, as git add, adds the files to the staging area, git reset HEAD removes the files from the staging area.
  - To amend the commit, use ``` git commit --amend ``` 
  - ### Rollback
  Let say you've made a commit, and now you want to revert it. You can do this using, ``` git revert HEAD ```, what will happen here is that git revert will create a new commit and reverse the changes. For example, a particular line was added in the commit and after the git revert HEAD, this line will be removed from the commit. So, in short git revert HEAD will create a new commit that is the opposite of everything in the given commit. Remember git revert HEAD will only revert the latest commit.
  - You can rollback to a specific commit by using: ``` git revert commit_id ```, you can get the commit_id by using ``` git log ```

- ### Branches
  - ``` git branch ``` shows a list of all the branches.
  - To create a new branch use: ``` git branch branch_name ```
  - To switch to another existing branch use: ``` git checkout branch_name ```
  - To create a new branch and switch to it immediately: ``` git checkout -b branch_name ```
  - To delete a git branch use: ``` git branch -d branch_name ```
  - To forcibly delete a branch: ``` git branch -D branch_name ```
  - Let say you are on a branch ``` master ``` and you want to merge ``` new-feature ``` branch into master, you can use: ``` git merge new-feature ```. One thing to remember here is that git merge, merges the files as well as the history of the branches.
  - To better understand the history of your commits use: ``` git log --graph --oneline ```
  - To abort a merge: ``` git merge --abort ```
