

# Gradle
- simplifies **manage android builds**
- there are 3 build **directive** 
  - **implementation**: for all build variant  
  - **testImplementation**: for JVM tests
  - **androidTestImplementation**: for Android UI tests

# Android Support Library 
- Added to support **backward comptability**: provide **new** fearture to **old** versions of android
- Add some helper class and utitlites specially for UI such as (**RecyclerView**, **CardView**)
- Add **testing** support library 
- As it **too big** it was **divided** into (**v4**  ,**v7** ,**v13**) and recently minumun supported is api **14**. 
- for example 
`implementation 'com.android.support:appcompat-v7:27.0.0'`

# AndroidX 
- Added to simplify **versioning** of support library
- so for appcomapt it became ` implementation 'androidx.appcompat:appcompat:1.0.0'`

# Android KTX
- part of **AndroidX**
- added to make android dev **more simpler** and use Kotlin language features.
- to use it: `implementation 'androidx.core:core-ktx:1.0.0'`  


# Testing 
- testing bacame a **core function** for app development to build a quality software.
- Android test require *physical device* or *emulator* which make tests take more time so we **divide** tests **into**: 
  - **logic-based** test: use JVM tests with JUnit framwork.
  - **android-based** tests: use instrumentaion tests.
   
- Each test is a function with `@Test` annotation 
- we use `Assert class` from `org.junit.Assert` as a **judge** to tests 
- exmaple 

    ``` kotlin 
    class ExampleUnitTest {
        
        
        @Test
        fun addition_isCorrect() {
            assertEquals(4, 2 + 2)
        }
    }

    ```

- There are many assert helper methods such as 
  - **assertEquals**: use `equals()` function 
  - **assertSame**: compare references 
  - **assertNull**: check if it is *null* 
    
- Also we should pay attention to test consistency(tests should not effect other tests , i.e each test run run with same state), this done by:
  - `@Before` **method** which used to **setup** environment for each test as it run before every test 
  - `@After` **method** which runs after each test used to **tearDown** resources 

# Automated UI tests 
- Now we need to do **android-based tests** that need Android environment. 
- will need 3 parts: 
  - **Tests** defined with `@Test`.
  - **Runner** that run tests on device: defined with `@RunWith` 
  - **Physical** device or **emulator** 


## To write test we will need
- **ViewMatcher**: provide *matcher* for android views, will be used to **specify** what **view** we need to interact with. 
  - examples (`withId`, `withText`, `isDisplayed`, `isChecked`, `equalTo`,  `allOf`, `anyOf`)
- **ViewActions**: used to perform action of a view 
  - exmaples (`click`, `typeText`, `replaceText`, `closeSoftKeyboard`)

- **NOTE**: we will need to run activity by using `ActivityTestRule` that run activity before each test 
- **ViewAssertions**: used to **check** specific action/view is **done** example (`matches` which accept one of **ViewMatchers** )
- exmaple 
  ``` kotlin 

  @RunWith(AndroidJUnit4ClassRunner::class)
  class ReminderViewModelTest {

      @get:Rule
      val activityRule = ActivityTestRule(MainActivity::class.java)

      @Test
      fun getReminders() {
          val reminderName = "TestAA"
          // open add activity
          onView(withId(R.id.fab)).perform(click())
          // type text
          onView(withId(R.id.edReminder)).perform(typeText(reminderName))
          // close kb
          closeSoftKeyboard()
          // click add button
          onView(withId(R.id.btnAdd)).perform(click())
          // go back
          pressBack()
          // make sure note is added
          onView(withText(reminderName)).check(ViewAssertions.matches(isDisplayed()))

      }
  }

  ```

## Test AdapterView items 
- It is special case to test data with **views** that use **Adapter** pattern such as (`ListView`, `Spinner`, etc)
- code 
  ``` kotlin 
  // first click so spinner open its dropDown list
  onView(withId(R.id.spinnerView)).perform(click())
  // select item
  onData(allOf(instanceOf(Reminder::class.java) , equalTo(ReminderItem("message")))).perform(click())
  ```
  - **Note**: add `import org.hamcrest.Matchers.*` to able to use (`allOf` ,`instanceOf`,`equalTo`)
  
- some cases with match,assert: 
  - ` onView(allOf(withId(R.id.fab) , isEnabled())).perform(click())`
  - ` onView(allOf(withId(R.id.fab) , isEnabled())).check(ViewAssertions.doesNotExist())`  

