# asynchronous programming techniques in Kotlin
## Preface
For decades, as developers we are confronted with a problem to solve - how to prevent our applications from blocking. Whether we're developing desktop, mobile, or even server-side applications, we want to avoid having the user wait or what's worse cause bottlenecks that would prevent an application from scaling.

There have been many approaches to solving this problem, including:

+ Threading

+ Callbacks

+ Futures, promises, and others

+ Reactive Extensions

+ Coroutines

## [Threading](https://kotlinlang.org/docs/async-programming.html#threading)
### Example 

```
fun postItem(item: Item) {
    val token = preparePost()
    val post = submitPost(token, item)
    processPost(post)
}

fun preparePost(): Token {
    // makes a request and consequently blocks the main thread
    return token
}
```

### Intro
Let's assume in the code above that preparePost is a long-running process and consequently would block the user interface. What we can do is launch it in a separate thread. This would then allow us to avoid the UI from blocking. This is a very common technique, but has a series of drawbacks:

### Cons

+ Costly. Threads require context switches which are costly.

+ NOT infinite. The number of threads that can be launched is limited by the underlying operating system. In server-side applications, this could cause a major bottleneck.

+ NOT platform-compatible. Some platforms, such as JavaScript do not even support threads.

+ NOT easy to debugging. Debugging threads and avoiding race conditions are common problems we suffer in multi-threaded programming.

## [Callbacks](https://kotlinlang.org/docs/async-programming.html#callbacks)
### Example

```
fun postItem(item: Item) {
    preparePostAsync { token ->
        submitPostAsync(token, item) { post ->
            processPost(post)
        }
    }
}

fun preparePostAsync(callback: (Token) -> Unit) {
    // make request and return immediately
    // arrange callback to be invoked later
}
```

### Cons

+ Difficulty of nested callbacks.
  
+ Error handling is complicated.

## [Futures, promises, and others](https://kotlinlang.org/docs/async-programming.html#futures-promises-and-others)
### Example

```
fun postItem(item: Item) {
    preparePostAsync()
        .thenCompose { token ->
            submitPostAsync(token, item)
        }
        .thenAccept { post ->
            processPost(post)
        }

}

fun preparePostAsync(): Promise<Token> {
    // makes request and returns a promise that is completed later
    return promise
}
```

### Cons
+ Different programming model.
+ Different APIs.
+ Specific return type.
+ Error handling can be complicated.

## [Reactive extensions](https://kotlinlang.org/docs/async-programming.html#reactive-extensions)
### Intro
Reactive Extensions (Rx) were introduced to C# by Erik Meijer. While it was definitely used on the .NET platform it really didn't reach mainstream adoption until Netflix ported it over to Java, naming it RxJava. From then on, numerous ports have been provided for a variety of platforms including JavaScript (RxJS).

> [!NOTE]
> Rx is simply the Observer Pattern with a series of extensions which allow us to operate on the data.
## Ref
[Asynchronous programming techniques (official docs)](https://kotlinlang.org/docs/async-programming.html)
