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

