# Lab Report 4

## Step 4 Log into ieng6
In step 4 we trying to login to the virtual machine, we use `ssh` command to connect to the virtual machine, with account name `cs15lfa23jv@ieng6.ucsd.edu`. I press `ssh` and using <Ctrl-C> to copy my account form the ucsd website, and use <Ctrl-V> paste it to the terminal, then press <enter> we connected to our terminal.
> Key pressed: `<Ctrl-C>, <enter>, <Ctrl-V>`
> Command used: `ssh`

![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/c42739cf-a792-46bb-bda4-c96017ed0627)

## Step 5 Clone your fork of the repository from your Github account
In step 5 we will use `git clone` command to clone the repository to the virtual machine, with the SSH URL `git@github.com:ziyexiaohei/lab7.git`. I pressed `git clone` and <space> then copy the ssh link, press <Ctrl-V> to paste the url into terminal with git clone, then we have the folder `lab7` inside the virtual machine.
> Key pressed: `<space>, <Ctrl-V>, <enter>`
> Command used: `git clone`
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/cfbbdd5a-a90d-4e01-921e-9fc72d7e4545)

## Step 6 Run the tests, demonstrating that they fail
In step 6 we need to run the test, first we need to go into the `lab7` folder, I used `cd lab7` to change my working directory to the `lab7` folder. Inorder to run the test I pressed `bash test.sh` and <enter> to run the test, and it shows that there is one failures.
> Key pressed：<Enter>
> Command used: `cd`, `bash` 
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/d1ad7ef7-5874-4b28-ad9c-0f1339a208be)

## Step 7 Edit the code file to fix the failing test
In step 7 we want to edit the code file `ListExamples.java` to fix the failing test. Inorder to edit the file we will use `vim`, I use the command `vim ListExamples.java` to enter `vim`, the cursor is on the first line, and the line we want to modeifly is on line 44, so we press <4><3><j> to go down, since the <j> is a vim key for <down> and the number in front
is how many times you want the command to reapte. And the character I want to change is in row 12 and the cursor is on row 1, thus we use <1><1><l>, the <l> key is special vim key for <right>. Now the cursor is on the character we want to change. Then we want to repalce the `1` with `2`, so I pressed <x> the key in vim used to delete character, and press <i> to enter
insert mod, and then press <2>. The key we pressed are `vim ListExamples.java`
> Key pressed: `<enter>, <4>, <3>, <j>, <1>, <l>, <2>, <x>, <esc>`
> Command used: `vim`
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/22c341d1-61db-4923-87a8-0562352c023e)


## Step 8 Run the tests, demonstrating that they now succeed
In step 8 we want to rerun the test and show that it run successfully, to exit insert mod, I pressed <esc> and the to save and quit vim, in normal mod I use <:><w><q>. And then we want to run `bash test.sh` again, I pressed <up><up><up>, The command `bash test.sh` is 3 lines up in the command history, so I use *up arrow* to access it, and then press <enter>.
> Key pressed: `<:>, <w>, <q>, <up>, <enter>`
> Command used: `bash`
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/3ebab904-0766-4633-9d8c-8f38d8d6b391)

## Step 9 Commit and push the resulting change to your Github account
In step 9 we want to commit and push the resulting change to my Github Account., we used `cd` to get back to home directory. and use `git add` to check the folder we want to commit, then use `git commit` to commit the folder and also use option `-m` to enter some messages indicates the change. Then use `git push` to push the resulting change to your Github account.
> Key pressed: `<enter>`
> Command used: `git add`, `cd`, `git commit`, `git psuh`
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/7b0d4c05-5343-4b23-b2f5-721d79ef6918)
