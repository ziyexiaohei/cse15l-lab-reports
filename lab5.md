## 1. Student Answer



Hello, I am working on the LIST-EXAMPLES-GRADER, and I've run into a puzzling issue that I can't seem to figure out. I've got a description of what I think might be the bug or at least some information about the code that's causing the failure.


This is the ouput of the error occur
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/813e8b85-7860-48ab-aa6c-134df816a0b5)


And this is the code for my grade.sh file
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/e73385b5-f3c2-416e-b221-0d08c31ba0d9)
This is directory before running the code:
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/07395dd9-d927-4a11-acf8-5f9591560b0a)

And this is directory after the running code :
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/c72b3a47-cee1-4087-9c6d-cce3d30ae4c5)

Description: I use the [Correct_file](https://github.com/ucsd-cse15l-f22/list-methods-corrected) as my input. From the grade.sh file I can see that it created a folder call grading-area, and it will clone the file student submitted into student-submission file. And it will check the name of the file to see did the student submit the correct file or not. I think the problem occur when we try to compile the file inside grading-area, error message showing that `package org.junit does not exist`, it should be some problem related to the junit file, I have tryed to reinstall the junit package, I dowload a new junit package to replaced the one we haved, but still showing the same error.


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


## 4. All the Resources
1. The file & directory structure needed: ![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/444cd30f-248a-42c6-8e0b-e961ccf8a7e9)
File needed is grade.sh and TestListExamples, and JUnit Library, the GradeServer and Server is not needed in this question.

2. The contents of each file before fixing the bug
grade.sh:
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission

echo 'Finished cloning'


if  [ -f "student-submission/ListExamples.java" ]; then
    echo "You submitted the correct file"
    else
    echo "You submitted the wrong File, please check"
fi

cp -r student-submission/ListExamples.java grading-area
cp TestListExamples.java grading-area

cd grading-area
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples

if [ $? -ne 0 ]; then
    echo "There is some error occur, please check your code"
else 
    echo "Your code is correct"
fi


# Draw a picture/take notes on the directory structure that's set up after
# getting to this point

# Then, add here code to compile and run, and do any post-processing of the
# tests
```
TestListExamples.java:
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }
}
```

3. The full command line to trigger the bug
`bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected`

4. A description of what to edit to fix the bug
To fix the Bug we could either copy the `lib` folder into grading-area,


or we can change the grade.sh script, change the relative path of the JUnit Library to absolute path.
