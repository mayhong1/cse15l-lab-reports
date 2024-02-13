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

## Sources Cited:
I found all these commmands through ChatGPT.

Here was more prompt: What are 4 commands that do the same thing as grep, and how do you use them?

Here was ChatGPT's answer: 
Sure, here are four commands that can perform similar tasks as `grep`, along with how to use them:

1. **egrep**:
   - Usage: `egrep [options] pattern [files]`
   - Example: `egrep "pattern" file.txt`
   - Explanation: `egrep` is similar to `grep`, but it supports extended regular expressions without needing to escape certain characters. You can use it to search for a pattern in one or more files.

2. **ack**:
   - Usage: `ack [options] pattern [files or directories]`
   - Example: `ack "pattern" file.txt`
   - Explanation: `ack` is a tool designed for programmers to search through code. It automatically ignores commonly ignored files and directories (like version control metadata), and highlights search results. It's particularly useful when searching through large codebases.

3. **ag (The Silver Searcher)**:
   - Usage: `ag [options] pattern [path]`
   - Example: `ag "pattern" file.txt`
   - Explanation: `ag` is a fast search tool optimized for codebases. It's written in C and is faster than both `grep` and `ack`. It ignores files and directories that are typically not relevant in programming projects, such as version control directories.

4. **rg (ripgrep)**:
   - Usage: `rg [options] pattern [path]`
   - Example: `rg "pattern" file.txt`
   - Explanation: `rg` is another fast search tool, written in Rust. It's designed to be faster than both `grep` and `ag`. It's particularly useful for searching through large codebases quickly and efficiently.

These commands work similarly to `grep` but may have different features or optimizations suited for specific tasks or environments.
