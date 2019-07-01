- we identify **expected values** and put **actual values** and JUnit do rest of work.
- easy to **run many tests** at **same time.**

## Example 

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


# Aggregate Tests into Suite 
- we can aggregate test classes and all together
- exmaple 
    ``` java
    import org.junit.runner.RunWith;
    import org.junit.runners.Suite;

    @RunWith(Suite.class) // speciffy runners. 
    @Suite.SuiteClasses({ // add test classes.
            TestMul.class,
            TestMul.class
    })
    public class TestSuit {

    }
   ```    

# Exception Handling tests
- we must test that program run **corrrectly when things goes wrong**.
- example 
    ``` java 
    import org.junit.Test;

    import java.util.ArrayList;

    public class TestException {

    // make sure that this method raise an exception from type of ArrayIndexOutOfBoundsException
    @Test(expected = IndexOutOfBoundsException.class)
    public void test(){
        new ArrayList<Object>().get(0);
    }
    }

    ```
# Ignor tests 
we may need to **ignor some tests** possible ways 
  - delete/**comment** method.
  - remove `@Test` annotation.
  - best one is use `@Ignore` annotation it **skips test** and **JUnit report it** at end of excution tests.  


# Paramaterized tests 
- **JUnit 4** they added another feature that **allows you run paramaterized tests**.
- This feature allows the developer to **run tests**, including **multiple values at one time**.


- ## Example 


    ``` java 
    import org.junit.Test;
    import org.junit.runner.RunWith;
    import org.junit.runners.Parameterized;
    import org.junit.runners.Parameterized.Parameters;

    import java.util.Arrays;
    import java.util.Collection;

    import static org.hamcrest.CoreMatchers.is;
    import static org.junit.Assert.assertThat;

    @RunWith(value = Parameterized.class)
    public class ParamaterizedTest {

        private int A ;
        private int B ;
        private int Expected ;

        public ParamaterizedTest(int a, int b, int expected) {
            A = a;
            B = b;
            Expected = expected;
        }
        // name attribute is optional, provide an unique name for test
        // multiple parameters, uses Collection<Object[]>
        @Parameters
        public static Collection<Object[]> data() {
            return Arrays.asList(new Object[][]{
                    // each one represent a data for single test A,B, Expected.
                    {1,2,3} ,
                    {2,3,5} ,
                    {3,4,7}
            });
        }
        @Test
        public void test(){
            assertThat(A+B , is(Expected));
        }
    }
    ```
