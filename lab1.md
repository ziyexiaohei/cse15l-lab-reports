# **Lab Report 1**
***

## Command `cd`
![Image](cs with no argument.png)
1. Using the Command with no argument
   The working directory is in home directory `/home` , which is in the home page, starting directory
   The cd command is to let you to change directory, when there is no argument it means that there is no output for the given command to process, which will end up returning to its initial directory, which is the home directory.
   The output doesn't haev any error occur, the output indicate that the working directory has return to home dierctory

2. Using the command with a path to directory as an argument
   The Working directory is in lecture1 directory `/home/lecture1`.
   The cd command allow us to change directory, this time we provide a path, which allow us to change our working directory.
   No error has occur, we successfully change our directory to the one we want.

3. Using the command with a path to a filen as an arugment
  The Working directory is in message file, `/home/lecture1/messages`.
  The cd command is for us to change directory, but this time the path we provide is to a file, thus the command cannot do the thing we want, error message pop up, remind us that the path we entered is not a directory, cd command cannot do anything with the path provided.
  Error has occur, Error message shows that the path I enter is not a directory. The error occur is becuase the cd command only allow us to change a directory, is for us to move between directorys, but the arugment we enter wants to change to a file instead of a directory, thsu the error message tells us that the path we enter is not a directory.

## Command `ls`
1. Using the command with no arugment
   The Working directory is in home directory
   The `ls` command will list all the file and folder inside the directory, the output we get is lecture1 the only folder inside the home directory.
   No eror messages pops up.
2. Using the command with a path to directory as an argument
   The Working the directory is in home direcotry
   The `ls` command will list all the file and floder inside the directory, this time we provide a path to a directory, thus it will list the file and floder in the directory we entered.
   No error occur.
3. Using the command with a path to file as an argument
   The working directory is in lecture1 folder, /home/lecture1
   The `ls` command will list all the file inside the given directory, when we use the command with a path to a file as an argument we will get a output only listing the file that we enter, istead all the file and folder inside the directory. Thus the output we have is only the file.
   No error.
## Command `cat`
1. Using the command with no argument
   The working directory is in home directory.
   The output we have acctually is empty, or it repeat what we entered, until we use `Control+D` represent "End Of Signal" to end it.    The `cat` command will print out the content of the file, in this case we didn't specific which file, so it will just wait for our input from the keyboard, then it will repeat the input and print out on the screen.
   No Error.
2. Using the command with a path to directory as an argument
   The working directory is in home direcotry
   The ouput shows that the path we entered is a direcotry, which is a error message, showing that the command `cat` cannot display the content of a directory, becasue the `cat` command will read the file and give its content as output, we cannot cat a directory.
   Error messages shows that the path I entered is a directory. The error occur becasue the `cat` command cannot read and display the content of a directroy, it can only read and display content of file as output.
3. Using the command with a path to file as an argument
   The working directory is in the messages folder, `/home/lecture1/messages`.
   The output is the text in the en-us.txt file, becasue the command `cat` will read the data of a file and give its content as output in your terminal.
   No error.
