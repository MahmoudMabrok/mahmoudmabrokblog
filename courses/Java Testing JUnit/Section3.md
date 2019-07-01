- we identify expected values and put actual values and JUnit do rest of work.
- easy to run many tests at same time.

example 

``` java 
import org.junit.Test;

import static org.junit.Assert.assertEquals;

public class TestSum {


    // annotte method with @Test
    @Test 
    public void testSum(){
        int n1 = 10 , n2 = 20 ;
        // use Assert to set Conditions to test, first value is expected, second is actual
        assertEquals(30 , n1+n2);
        // there are several methods, assertEquals, assertSame, assertNull.  
    }
}


```


