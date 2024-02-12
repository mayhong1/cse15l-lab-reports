1. Failure Inducing Input:

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test
  public void testReverseInPlace() {
    int [] input = {1, 2, 3, 4};
    int [] expected = {4, 3, 2, 1};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(expected, input);
  
  }
}
```
