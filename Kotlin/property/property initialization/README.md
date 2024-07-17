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

| item                | Lazy initialization | Late initialization |
----------------------| ------------------- | ------------------- |
| keyword             | `lazy`                | `lateinit`            |
| can declare variable with |                 | `val`                 | `var`                 |
| example                    | `val myLazyString: String by lazy { "Hello" }`                    | `lateinit var subject: TestSubject`                    |
| behaviour | `by lazy { ... }` defines the only initializer for the property | `lateinit var` can be initialized from anywhere the object is seen from, e.g. from inside a framework code |
| altered scenario | It can be initializes in any initialization scenarios in class (i.e. anywhere within `init {}` | It can only be altered by overriding the property in a subclass
| backing field | `by lazy { ... }` does **NOT** have backing field, the value is stored once it is calculated. | `lateinit var` has a backing field which stores the value
| thread-safe | Yes, thread-safe by default. | No |
| Why thread-safe (or not)? | Since it guarantees that the initializer is invoked at most once (but this can be altered by using another lazy overload). | Since it's up to the user's code to initialize the property correctly in multi-threaded environments. |
| How to check it is initialized | `isInitialized()` | `property::isInitialized` (added in Kotlin 1.2) | 

## Ref
Lazy initialization v.s. Late initialization

https://stackoverflow.com/questions/36623177/property-initialization-using-by-lazy-vs-lateinit
