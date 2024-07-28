# Coroutine in Kotlin
## Example 
### Example 1

```
// 1. this call starts a new coroutine (let's call it C1).
//    If there were code after it, it would be executed concurrently with
//    the body of this async
async {
    ...
    // 2. this is a regular function call, so we go to computation()'s body
    val deferred = computation()
    // 4. we're back from the call to computation, about to call await()
    //    Because await() is suspendING, it suspends coroutine C1.
    //    This means that if we had a single thread in our dispatcher, 
    //    it would now be free to go execute C2. With multiple threads,
    //    C2 may have already started executing. In any case we wait 
    //    here for C2 to complete.
    // 7. once C2 completes, C1 is resumed with the result `true` of C2's async
    val result = deferred.await() 
    ...
    // 8. C1 can now keep going in the current thread until it gets 
    //    suspended again (or not)
}

fun computation(): Deferred<Boolean> {
    // 3. this async call starts a second coroutine (C2). Depending on the 
    //    dispatcher you're using, you may have one or more threads.
    // 3.a. If you have multiple threads, the block of this async could be
    //      executed in parallel of C1 in another thread
    // 3.b. If you have only one thread, the block is sort of "queued" but 
    //      not executed right away (as in an event loop)
    //
    //    In both cases, we say that this block executes "concurrently"
    //    with C1, and computation() immediately returns the Deferred
    //    instance to its caller (unless a special dispatcher or 
    //    coroutine start argument is used, but let's keep it simple).
    return async {
        // 5. this may now be executed
        true
        // 6. C2 is now completed, so the thread can go back to executing 
        //    another coroutine (e.g. C1 here)
    }
}
```

#### explanation

The outer async starts a coroutine. When it calls computation(), the inner async starts a second coroutine. Then, the call to await() suspends the execution of the outer async coroutine, until the execution of the inner async's coroutine is over.

You can even see that with a single thread: the thread will execute the outer async's beginning, then call computation() and reach the inner async. At this point, the body of the inner async is skipped, and the thread continues executing the outer async until it reaches await(). await() is a "suspension point", because await is a suspending function. This means that the outer coroutine is suspended, and thus the thread starts executing the inner one. When it is done, it comes back to execute the end of the outer async.


## Q&A
### Q1:
Does suspend mean that while outer async coroutine is waiting (await) for the inner computation coroutine to finish, it (the outer async coroutine) idles (hence the name suspend) and returns thread to the thread pool, and when the child computation coroutine finishes, it (the outer async coroutine) wakes up, takes another thread from the pool and continues?

### A1:
Yes, precisely.

The way this is actually achieved is by turning every suspending function into a state machine, where each "state" corresponds to a suspension point inside this suspend function. Under the hood, the function can be called multiple times, with the information about which suspension point it should start executing from (you should really watch the video I linked for more info about that).

## Ref
[what does the suspend function mean in kotlin coroutine](https://stackoverflow.com/questions/47871868/what-does-the-suspend-function-mean-in-a-kotlin-coroutine)
