Hello, I am working on the LIST-EXAMPLES-GRADER, and I've run into a puzzling issue that I can't seem to figure out. I've got a description of what I think might be the bug or at least some information about the code that's causing the failure.


This is the ouput of the error occur
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/195484f3-42dc-4425-9e6d-eec70aac9ed4)


And this is the code for my grade.sh file
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/49b78b96-d6ca-4987-9287-12a656dd0b28)
And this is what it does to the directory:
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/c8fe0ab5-188a-4044-a699-39f2b1abe2f5)

Description: From the grade.sh file I can see that it created a folder call grading-area, and it will clone the file student submitted into student-submission file. And it will check the name of the file to see did the student submit the correct file or not. I think the problem occur when we try to compile the file inside grading-area, error message showing that `package org.junit does not exist`, it should be some problem related to the junit file, I have tryed to reinstall the junit package, I dowload a new junit package to replaced the one we haved, but still showing the same error.



Hi,

Based on the information you provided, it seems like the issue could indeed be related to the absence of the JUnit library in the grading-area directory. When you're compiling and running Java files in a specific directory, that directory needs to include all the dependencies, including JUnit.

You can modify your grade.sh script to copy the JUnit library into the grading-area directory before compiling and running the tests. Here is one way you can do it:
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/2487f883-392a-4517-91d9-20eee8f85b8c)

Here you can use `cp` with option `-r` to copy the entire lib folder into grading-area. This should ensure that both your source files and the necessary JUnit libraries are present in the same directory when compiling and running the tests.

When we compile and run the java file, we need to know where to find the classes and libraries that your code depends on, the code you have for compile the java file is `javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java` which the `lib/hamcrest-core-1.3.jar` tells the compiler where the library are, and in your code, you decided to change your path into grading-area and compile there, then there does not have a lib folder contain all the JUnit Library, that is the reason why your error message saying that org.junit does not e
