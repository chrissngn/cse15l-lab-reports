# Lab Report 5 - Putting it all together

## Part 1 - Deubugging Scenario

**1. Original post from student:**
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

**2. Response from TA:**
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
## Part 2 - Reflection
