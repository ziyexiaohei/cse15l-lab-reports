# Part 1 - Bugs
1. failure- including input for the Program
* For ReverseInPlace method:
Test Code:
```
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = { 1,2,3,4,5,6,7,8 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 8,7,6,5,4,3,2,1 }, input1);
	}

```
Associated code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
2. Input that doesn't induce a failure
   Test Code:
```
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```
Associated code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
3.Symptom
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/d18383cf-a038-4a3f-b8dc-71b37c9700cc)


4.Fix
Before:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp= arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i -1] = temp
    }
  }
```
Explaination: In the code before we fix, it will only reverse half of of the array, for example {1,2,3,4,5,6,7,8}, the code will replace the first 4 element of the arrray with the last 4 element, which make the array into {8,7,6,5,5,6,7,8} in the fourth element we want to have is 4, but according to the code it will be 5, because, after we updated the array the fourth element will be replace by the third element, in the new array fourth element and fifth element is the same, thus error occur.

<br>

Solution: The solution to this bug is that we can just swap the relative element, we store the element of array we going to replace into temp, in our example we want to replace element[0] with element[7], we store element[0] into temp, replace it with element[7], then put the value store in temp into element[7]. By doing this we can keep track of every element, and we only need to iterate half of the array, and the problem will be solved, since we not only updated the first half element of the array, and also we updated the last half of array.


# Part 2: `find` command: The `find` command is use to search for files in a directory hierarchy
##command-line options:
1. `-name`: Using find with -name we are able to find the file with certain names, and if we want to find file name contains come letter we can just add double quotation marks aroud them, such as `"*.txt"` will list all the file end with .txt, just use `find <path> -name file.txt`, which will list all the file name file.txt.

* `find <path> <path> <filename>` on file
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$  find /c/Users/Bobby/Documents/GitHub/docsearch/technical/911report /c/Users/Bobby/Documents/GitHub/docsearch/technical/government/Alcohol_Problems -name "*.txt"     
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-1.txt   
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-10.txt  
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-11.txt  
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-12.txt  
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.1.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.2.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.3.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.4.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.5.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-2.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-3.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-5.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-6.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-7.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-8.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-9.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/preface.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/government/Alcohol_Problems/DraftRecom-PDF.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/government/Alcohol_Problems/Session2-PDF.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/government/Alcohol_Problems/Session3-PDF.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/government/Alcohol_Problems/Session4-PDF.txt
```
In this example we were using the command with two paths `find <path> <path> <filename>` that list all the file end in .txt in the given directory, the * means any character of any length, thus using *.txt with find will list all the path of file end in .txt. By using the -name expression, we are able to enter find some file that has a certain file name. When we want to find some file with certain file name in different directory, we can use this form with two path, which can save us a lot of time, we do not need to switch to diffrent directory.

* `find -name <directory ` on direcotry
  ```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical/911report (main)
$  `find -name <directory name>`
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$  find -name 911report
./911report
```
This command will help us to find all the file and directory that is called 911 report. This command is useful when we are trying to see does there a folder that we want in our current working directory.
* source: https://kb.iu.edu/d/admm
<br>
2. `-type`: the comman-line optiopn  `-type` will allow us to find certain type of file.
* `find -type f` on file
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find /c/Users/Bobby/Documents/GitHub/docsearch/technical/911report -type f
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-1.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-10.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-11.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-12.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.1.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.2.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.3.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.4.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-13.5.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-2.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-3.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-5.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-6.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-7.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-8.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/chapter-9.txt
/c/Users/Bobby/Documents/GitHub/docsearch/technical/911report/preface.txt
```
This time we will be using the `-type` command-line expression, where it allow us to find and list all the type of file or directory that we want, in this example it will be all the files. The `f` stand for file which will just list all the file in current working directory. This command is useful, when our working directory has both files and folders, and we want to calculate the amount of file it has, this command is useful in that situration to only listing the files, without the foldres.

* `find -type d` on directory
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```
This command is used to list all the directory in our current working directory, in this command the `d` stand for directory, which will help to identify what type of file we want to find. This command is useful when we are looking for folders, and we can combined this wil `-name` to find folder, and ignore the file with the same name, it will be more efficient compared to `find`, which list all the files, and using `-name` when there are multiple file with same name.
* source: https://kb.iu.edu/d/admm
<br>

3. `-size`: command option that allows user to find a specific size of file, usually is in 512-byte block if no suffix is used.
* `find -type f -size 100b` on file
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find -type f -size 100
./biomed/1471-2156-3-17.txt
./biomed/1472-684X-1-5.txt
./biomed/gb-2001-2-8-research0030.txt
./biomed/gb-2002-3-5-research0025.txt
./government/Gen_Account_Office/Paper_Walker11-2002_acpro122.txt
```
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/8f70de82-2f07-40dc-b1ed-50192cce8212)

This command we used two command line option, to help us to have shorter output, the `-type f` is to help us only list the files, and `-size` will list files that is excally the size we assig, combining these two will only list files that are excaly the size I want. As the picture shows the file is 53,248 bytes, when we did not have a suffix in the command, the default suffix is `b` which is 512 bytes, 100*512 bytes is 51200 bytes, which is almost the same. This command is useful, when we trying to delete file that are certain size, this will be very useful. Further more you can add - or + infront the <sizeassign> to list files that are below or above that size, `find -size -100M` list file under 100Mb. 

* `find -type d -size -10M` on directory
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find -type d -size 0M
.
./911report
./biomed   
./government
./government/About_LSC
./government/Alcohol_Problems  
./government/Env_Prot_Agen     
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm    
./plos
```
This command will list all the directroy that has a size equal to 0 byte, which is empty, but thats not true. From this example we can see that the `-size` does not work on directory, it cannot filtering directories by their size, it can only do that with files; Therefore, this expression is not useful.

* source: https://kb.iu.edu/d/admm
  <br>
4.`-mtime`: This expression allow user to find file or directory that got modified at the specified time, takes day as unit.

* `find -type f -mtime -7` on file
```
Bobby@DESKTOP-85GLBDM MINGW64 ~/Documents/GitHub/docsearch (main)
$ find ~/Documents/GitHub/docsearch//technical/911report/ -type f -mtime -7
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-1.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-10.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-11.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-12.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-13.1.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-13.2.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-13.3.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-13.4.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-13.5.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-2.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-3.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-5.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-6.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-7.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-8.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/chapter-9.txt
/c/Users/Bobby/Documents/GitHub/docsearch//technical/911report/preface.txt
```
This command will find all the file that is in the given directory that got modified in the last 7 days, the expression `-mtime` is stand for modified time, which takes day unit. This is very useful because when we are working in a company, we take over the project, we want to find the file that they havd been working on, we can just use this command and we can just see what file did they modified in the past 1 days, or so. Similarly we can use `-mmin` that takes min as unit.

* `find -type d -mtime -7` on directory
```
$ find -type d -mtime -7
.
./.git
./.git/hooks
./.git/info
./.git/logs
./.git/logs/refs
./.git/logs/refs/heads
./.git/logs/refs/remotes
./.git/logs/refs/remotes/origin
./.git/logs/refs/remotes/upstream
./.git/objects
./.git/objects/info
./.git/objects/pack
./.git/refs
./.git/refs/heads
./.git/refs/remotes
./.git/refs/remotes/origin
./.git/refs/remotes/upstream
./.git/refs/tags
./lib
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
This command will find all the folders that got modeified in the past 7 days. This is very useful because it can help us to save a lot of time when we are trying to organize files, and when we want to do some modification to the fiels that were being modified in the a certain day, either before a period of time, or after a period of time. Instead of typing it all out, we can just this expression to done thing more quicker.

* source: https://kb.iu.edu/d/admm
