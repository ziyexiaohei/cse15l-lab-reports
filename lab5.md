## 1. Student Answer



Hello, I am working on the LIST-EXAMPLES-GRADER, and I've run into a puzzling issue that I can't seem to figure out. I've got a description of what I think might be the bug or at least some information about the code that's causing the failure.


This is the ouput of the error occur
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/195484f3-42dc-4425-9e6d-eec70aac9ed4)


And this is the code for my grade.sh file
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/49b78b96-d6ca-4987-9287-12a656dd0b28)
And this is what it does to the directory:
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/c8fe0ab5-188a-4044-a699-39f2b1abe2f5)

Description: From the grade.sh file I can see that it created a folder call grading-area, and it will clone the file student submitted into student-submission file. And it will check the name of the file to see did the student submit the correct file or not. I think the problem occur when we try to compile the file inside grading-area, error message showing that `package org.junit does not exist`, it should be some problem related to the junit file, I have tryed to reinstall the junit package, I dowload a new junit package to replaced the one we haved, but still showing the same error.


## 2. TA Respond 

Hi, 
Based on the information you provided, it appears that the JUnit package is not being recognized during compilation, as showed by the error message "org.junit does not exist"

I suggest carefully reviewing the grading-area.sh script, payin attention to the lines related to JUnit. Verify if the path specified tells the JVM and Java compiler about where the JUnit library. Also you can think about what do you need to do when there is some file missing in your directory.

Take a moment to go over the JUnit-related lines in your script, and confirm if the path is set up correctly. If you encounter any problems, feel free to share those specific script lines, and we can work together to address them.




## 3. Student Respond








Hello, 

Thanks for the help, after looking through the grade.sh script, I find what the bug is. When I compile and run Java files in a specific directory, that directory needs to include all the dependencies, including JUnit.

When I compile and run the java file, I need to know where to find the classes and libraries that my code depends on, the code I have to compile the java file is `javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java` which the `lib/hamcrest-core-1.3.jar` tells the compiler where the library are, and since I decided to change the working directory into grading-area and compile there, it does not have JUnit Library inside `lib` folder, that is the reason why my error message saying that org.junit does not exist. From what you said there seems to have two solution to fix this, either I change the relative path to JUnit to absolute path or I can just copy the `lib` folder into grading-area.

I modify my grade.sh script to copy the JUnit library into the grading-area directory before compiling and running the tests.
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/2487f883-392a-4517-91d9-20eee8f85b8c)

![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/49f22ea2-40e1-4631-af95-a77cc30ce151)
