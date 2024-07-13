# import statement in Kotlin
## Prequisite
Fully understand of package in Kotlin.

You can see my notes at Github.

https://github.com/40843245/Kotlin_Tutorial/tree/main/Kotlin/package%20and%20import/package

## Import statement 
To import a function or class etc from a package. One can use import statement as following.

    import packagename.class1 

For fully understand, see the following example.

### Example

Continue the example at the above note.

    package org.example
    
    fun printMessage() { /*...*/ }
    class Message { /*...*/ }
    
    // ...

In this example, the full name of class Message is org.example.Message.

If one wants to create the Message object. One can either directly instantiate it

    val message = org.example.Message

or import the Message class of org.example package and then instantiate it

    import org.example.Message 
    // ...
    val message = Message

or import all functions and classes of org.example package (since importing all functions and classes also imports the Message class, of course) and then instantiate it

    import org.example.*
    // ...
    val message = Message

## Import statement and alias it
Contiune the above example, if one wants to import Message class and give alias it as TestMessage. Write the following.

    import org.test.Message as TestMessage // TestMessage stands for 'org.test.Message'
    
## Ref
From Kotlin docs,

https://kotlinlang.org/docs/packages.html
  
