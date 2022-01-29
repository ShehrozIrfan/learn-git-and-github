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
