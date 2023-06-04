# Lab Report 5 - Putting it all together

## Part 1 - Deubugging Scenario

**1. Original post from student**
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/d19ce521-8427-4b3b-84b3-783edd1cde93)
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/ceb9e5ad-120f-46b9-87ae-6b5a314f68eb)
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/cc4aae55-7287-4904-a897-e13da75fa66f)
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/6370df36-1dd5-42b8-a65a-52b2e8e420b3)

**Screenshots from student:**
ListExamples.java - 
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/068b24e7-332a-4bf7-ab48-89e7d29c22bd)

ListExamplesTest.java - 
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/ded009d5-adf6-4e8d-b512-28e27709b16f)

`bash test.sh` - 
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/92ac947a-ac62-459b-a55c-9480b454b6f6)

**2. Response from TA**
Hello Christine,

It seems that the terminal is reporting an incompatible types error inside of the ListExamples.java on line 15 of the filter() method, `results.add(0,sc)`. sc is has the type of StringChecker, however, the result.add() takes in an integer index and a string which means that calling sc in results.add() will cause an error since sc is not a string type.
```
[cs15lsp23ko@ieng6-202]:lab7:346$ bash test.sh
ListExamples.java:15: error: incompatible types: StringChecker cannot be converted to String
        result.add(0, sc);
                      ^
Note: Some messages have been simplified; recompile with -Xdiags:verbose to get full output
1 error
JUnit version 4.13.2
..
Time: 0.013

OK (2 tests)
```

To fix this bug you will need to replace `sc` with `s` as `s` is a string type:
```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
```
Your test cases should pass as they have been and the error regarding incompatible types should be resolved.

**3. Student result from trying TA's debug instructions**
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/fa788a24-2a85-4187-8c17-4bf3e4ea8105)

![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/80df1468-bcad-4ffa-a81a-b8f56274e64c)

**4. Information about the set up**
Lab 7 Repository: https://github.com/chrissngn/lab7.git

**Files Before Bug Fixes:**
**ListExamples.java -**
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, sc);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index2 += 1;
    }
    return result;
  }
//this is a comment

}                                                                                                                                                 15,24
```
**ListExamplesTests.java - **
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
        @Test(timeout = 500)
        public void testMerge1() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
                assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
        }

        @Test(timeout = 500)
        public void testMerge2() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
                assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }

}
```
**Test.sh -**
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

**Command that induced the bug:**
`bash test.sh`

**Description of edits to fix bugs**
The only file that needs to be edited to fix the bug is the ListExamples.java file. The bug is on line 15 and it is an incompatible type error. The variable being call `sc` is of the type StringChecker when results.add(int,string) takes in only ints and string. To fix this bug `sc` need to be replaced with `s` which is a string inside of `sc`. After fixing the bug the error should be resolved and all the junit tests should pass.

**ListExamples.java after fix:**
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
        //note the change from sc to s
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index2 += 1;
    }
    return result;
  }
//this is a comment

}                                 
```

**Terminal after fixes:**
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/3e85ffd8-12d9-4d05-8f3e-da88af068694)

## Part 2 - Reflection
The second half of this quarter we worked with vim, bash scripts, and a lot with the command line. The topic I found the coolest was the autograding topics because I was able to see assignments from the TA's point of view. Working with the bash script language was a bit challenging because I wasn't too familar with the syntax but I found the concept of using bash script to grade mock assignments to be enlightening. Before taking this class I often heard the term vim but had no idea what it is was. During the second half of this quarter I learn what vim was and how to use it which was amazing because I can now say that I know how to use vim(kind of lol) and understand the context of it in future conversations.
