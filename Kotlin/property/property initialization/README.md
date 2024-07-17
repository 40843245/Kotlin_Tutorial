# property initialization
## Lazy initialization (lazy keyword)
### Example

    public class Hello {
       val myLazyString: String by lazy { "Hello" }
    }

## Late initialization (lateinit keyword)
### Example

    public class MyTest {
       lateinit var subject: TestSubject
       @SetUp fun setup() { subject = TestSubject() }
       @Test fun test() { subject.method() }
    }

## Lazy initialization v.s. Late initialization

| Lazy initialization | Late initialization |
| ------------------- | ------------------- |
|                     |                     |
| ------------------- | ------------------- |
|                     |                     |

## Ref
Lazy initialization v.s. Late initialization

https://stackoverflow.com/questions/36623177/property-initialization-using-by-lazy-vs-lateinit
