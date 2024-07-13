# import statement in Kotlin
## Prequisite
Fully understand of package in Kotlin.

You can see my notes at Github.

https://github.com/40843245/Kotlin_Tutorial/tree/main/Kotlin/package%20and%20import/package

## Example

Continue the example at the above note.

    package org.example
    
    fun printMessage() { /*...*/ }
    class Message { /*...*/ }
    
    // ...

In this example, the full name of class Message is org.example.Message.

If one wants to create the Message object. One can either directly instantiate it

    val message = org.example.Message

or import org.example package and then instantiate it

    import org.example
    // ...
    val message = Message

## Ref
From Kotlin docs,

https://kotlinlang.org/docs/packages.html
  
