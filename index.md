Failure Inducing & Non-Failure Inducing Input:

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

The symptom:
![screenshot1](screenshot1.png)

The bug:
Before:
After:

