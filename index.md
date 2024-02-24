# Part 1

## Failure Inducing & Non-Failure Inducing Input:

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  // this test induces failure
  @Test
  public void testReverseInPlace1() {
    int [] input = {1, 2, 3, 4};
    int [] expected = {4, 3, 2, 1};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(expected, input);
  }
  // this test does not induce failure
  @Test
  public void testReverseInPlace() {
    int [] input = {3, 2, 2, 3};
    int [] expected = {3, 2, 2, 3};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(expected, input);
  }

}
```

##The symptom:
![screenshot1](screenshot1.png)

## The bug:

### Before Fixing:
![screenshot2](screenshot2.png)

### After Fixing:
![screenshot3](screenshot3.png)

In the before screenshot, the values in the array were being directly modified. Once `i` reached `arr.length/2`, the first half of the array has been modified. So, when you set the values in the second half of the array to the values in the first half of the array, those values are the modified values (not the original values), resulting in the bug. To fix this, you could create a copy of the array. Then, in each iteration of the loop you would set `arr[i]` to `arrCopy[arr.length - 1 - i]`; in this version, the values are the original values because you are setting it to an original version of the array and not a modified version.

# Part 2

## `grep` command line options

### grep -l

#### grep -l Example 1
Working directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical

Command: `grep -l "California" 911report/*`

Output: 
```
911report/chapter-11.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-3.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-8.txt
```

Description: The -l option makes it so that grep prints out every file that contains a specific pattern, which is useful when you want to search for files that contain a certain phrase. So, in this case, every file that contains the word "Calfiornia" inside the 911report/ directory is printed out.

#### grep -l Example 2
Working directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government

Command: `grep -l "NIAAA" alcohol_problems/*`

Output:
```
alcohol_problems/DraftRecom-PDF.txt
alcohol_problems/Session2-PDF.txt
alcohol_problems/Session4-PDF.txt
```

Descrption: Every file inside the /government directory that contains the word "NIAAA" is printed out because the -l option makes it so that grep prints out every file that contains a certain pattern. This is useful when you are just searching for files that contain a certain phrase.

### grep -c

#### grep -c Example 1

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/Gen_Account_Office

Command: `grep -c "United States" ffm.txt`

Output:
```
7
```

Description: the -c option for grep has it print out the number of lines within a text file that contains a certain phrase, which is useful when you want to know the number of occurences. In this case, 7 lines contain the phrase "United States" in ffm.txt

#### grep -c Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/biomed

Command: `grep -c "smoking" 1468-6708-3-1.txt`

Output:
```
7
```

Description: The number of lines that contain the phrase "smoking" in "1468-6708-3-1.txt" is printed out, which in this case is 7. This is because the -c option has grep print out the number of lines within a text file that contains a specificed pattern. 

### grep -o

#### grep -o Example 1

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/911report

Command: `grep -o "New York" chapter-9.txt`

Output:
```
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
New York
```

Description: The -o option makes it so that grep prints every line in the specified file that contains a specified pattern, but only the matching part of the line; this is useful when you don't want the entire line but just the matching part to be printed. Here, all the matching parts of the lines that contain "New York" in chapter-9.txt was printed.

#### grep -o Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/media

Command: `grep -o "Illinois" Annual_Fee.txt`

Output: 
```
Illinois
Illinois
Illinois
Illinois
Illinois
Illinois
Illinois
Illinois
```

Description: The -o option makes it so that grep prints every line in the specified file that contains a specified pattern, but only the matching part of the line; this is useful when you don't want the entire line but just the matching part to be printed. Here, all the parts of the lines that contain "Illinois" in Annual_Fee.txt was printed.

### grep -n

#### grep -n Example 1

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/media

Command: `grep -n "lawyer" Barnes_new_job.txt` 

Output:
```
11:(unpaid) lawyer at the Atlanta Legal Aid Society.
37:lawyer for every 10,500 eligible poor people.
49:state's ethical rules include language indicating lawyers'
54:percent of the state's 23,598 active lawyers reported meeting the
59:people are served by only 24 percent of the state's lawyers.
72:counsel. Why? Because competent lawyers in the corporate practice
```

Description: The -n option makes it so that grep prints the line number and contents of every line that contains the phrase "lawyer" in Barnes_new_job.txt. This is useful if you want the line number of every line that contains a certain phrase in a file.

#### grep -n Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/plos

Command: `grep -n "nations" journal.pbio.0020001.txt`

Output: 
```
204:        them. There are now examples in which research on priority areas for the developing nations
222:        direction. The extremely high scientific productivity of many developing nations, corrected
224:        to the sciences will be an excellent investment by developing nations in terms of
```

Description: The -n option makes it so that grep prints the line number and contents of every line that contains the phrase "nations" in journal.pbio.0020001.txt. This is useful if you want the line number of every line that contains a certain phrase in a file.

## Sources Cited:
I found all these commands through this website: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
