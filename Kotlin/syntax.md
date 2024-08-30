# Kotlin
## syntax
### entry point

> [!CAUTION]
> In kotlin, each `.kt` must have exactly one entry point. Otherwise, one will get compiler error.

> [!CAUTION]
> In kotlin, an entry point is a `main` function.
>
> ```
> fun main(){
>   <mainBody>
> }
> ```

For example, see `CH1 - print in console` in my example code[^1].

### logical operator

| symbol | keyword | description |
| :- | :- | :- |
| `&&` | `and` | returns `true` iff all elements are evaluated to `true`. |
| `\|\|` | `or` | returns `true` iff one of elements is evaluated to `true`. |
| `!` | `not` | returns `true` iff the only one element is `false`. `false` to `true`. `true` to `false` |

| symbol | x | expression | returned result |
| :- | :- | :- | :- |
| `!` | `true` | `!x` | `false` | 
| `!` | `false` | `!x` | `true` | 

| symbol | x | y | expression | returned result |
| :- | :- | :- | :- | :- |
| `&&` | `true` | `true` | `x && y` | `true` | 
| `&&` | `false` | `true` | `x && y` | `false` | 
| `&&` | `true` | `false` | `x && y` | `false` | 
| `&&` | `false` | `false` | `x && y` | `false` | 

| symbol | x | y | expression | returned result |
| :- | :- | :- | :- | :- |
| `\|\|` | `true` | `true` | `x \|\| y` | `true` | 
| `\|\|` | `false` | `true` | `x \|\| y` | `true` | 
| `\|\|` | `true` | `false` | `x \|\| y` | `true` | 
| `\|\|` | `false` | `false` | `x \|\| y` | `false` | 



For example, see `CH6 - logical operator` in my example code[^1].

### conditional statement
#### if 

+ The first form also the basic form as follows.

Iff the condition in `if` -- `<condition1>` is true, the expressions in `if` block -- `<expressions1>` will be evaluated.

```
if(<condition>){
  <expressions1>
}
```

+ The second form as follows.

Similar to first form.

Iff the condition in `if` -- `<condition1>` is true, the expressions in `if` block -- `<expressions1>` will be evaluated.

Otherwise, the expressions in `else` block -- `<expressions2>` will be evaluated.

```
if(<condition1>){
  <expressions1>
}else{
  <expressions2>
}
```

+ The third form as follows.

Similar to second form. 

> [!TIP]
> One can think it contains another `if-else` statement in first `else`block.

Iff the condition in `if` -- `<condition1>` is true, the expressions in `if` block -- `<expressions1>` will be evaluated.

Otherwise, iff the condition in `else if` -- `<condition2>` is true, the expressions in `else if` block -- `<expressions2>` will be evaluated.

Otherwise, the expressions in `else` block -- `<expressions3>` will be evaluated.

```
if(<condition1>){
  <expressions1>
}else if(<condition2>){
  <expressions2>
}else{
  <expressions3>
}
```

We can expand it to more `else if ` on `if` statement.

> [!IMPORTANT]
> In Kotlin, all blocks has only one expression, then the expression will be evaluated value then ***returned***. See fourth form and fifth form.

+ The fourth form as follows.

If `<condition1>` is evaluated to true, then the only one expression `<expression1>` will be evaluated and ***returned***.

Otherwise, the only one expression `<expression2>` will be evaluated and ***returned***.

```
<variableName> = if(<condition1>) <expression1> else <expression2>
```

or equivalently

```
<variableName> = if(<condition1>) {
  <expression1>
}else{
  <expression2>
}
```

+ The fifth form as follows.

If `<condition1>` is evaluated to true, then the only one expression `<expression1>` will be evaluated and ***returned***.

Otherwise, if `<condition2>` is evaluated to true, the only one expression `<expression2>` will be evaluated and ***returned***.

Otherwise, the only one expression `<expression3>` will be evaluated and ***returned***.

```
<variableName> = if(<condition>) <expression1> else if (<condition2>) <expression2> else <expression3>
```

or equivalently

```
<variableName> = if(<condition1>) {
  <expression1>
} else if (<condition2>) {
  <expression2>
}else {
  <expression3>
}
```

We can expand it to more `else if ` on `if` statement.

> [!CAUTION]
> If the `if` statement is used to return value, then all pathes among these block must return same type.
>
> Thus, the `else` and its block can ***NOT*** be omitted.

For example, see `CH7 - conditional statement` in my example code[^1].

### loop
#### for

It will first evaluate the condition in `for` -- `<condition>`. `<condition>` is evaluated to true iff the block in `for` -- `<body>` will be executed. 

After each execution of the block in `for` -- `<body>`, it will iterate to the next element of variable in .

```
for(<condition>){
  <body>
}
```

where 

```
<condition> contains a variable for iteration.
```

It is usually to see `in` keyword in `for` loop.

The common use cases of `for` as follows:

+ use case 1:
  
```
var i : Int = 0
for(i in 0..10){
  //TODO
}
```

+ use case 2:
  
```
val list1 = mutableListOf(2,4,6,8,10)
var elem : Int = 0
for(elem in list1){
  //TODO
}
```

+ use case 3:
  
```
val array1 = arrayOf(2,3,4,5,6,12)
var elem : Int = 0
for(elem in array1){
  //TODO
}
```

+ use case 4:
  
```
val map1 = mapOf( 'A'-> 20, 'B' -> 21)
var elem : Int = 0;
for(elem in map1){
  //TODO
}
```

For example, see `for` in my example code[^1].

#### while

It will first evaluate the condition in `while` -- `<condition>`. `<condition>` is evaluated to true iff the block in `while` -- `<body>` will be executed. 

```
while(<condition>){
  <body>
}
```
For example, see `while` in my example code[^1].

#### do while

It will first execute the block `<body>`in `do while` . Then it will evaluate the condition in `do while` -- `<condition>`. `<condition>` is evaluated to true iff the block in `do while` -- `<body>` will be executed. 

```
while(<condition>){
  <body>
}
```

> [!CAUTION]
> Watch out the order of condition check in loop.
>
> The block in `while` may NOT be executed.
>
> But the block in `do while` must be always executed at once.

For example, see `do while` in my example code[^1].

### range
In Kotlin, one can return an iterator as arithmetic sequence (等差數列). Such as `(1,2,3,4,5,6)`, `(3,5,7,9)`,`(10,8,6)`,`('A','B','C','D')`.

+ In comparison:

There are two symbols `..` and `..<` (`until`)
  
Given these numbers `a`,`b`, and `x` where `a` refers lower bound `b` refers upper bound.

- `..` : `a .. b` is equivalent to  `a <= x && x <= b`. (both inclusive.)
- `..<` or `until` : `a..< b` is equivalent to `a <= x && x < b` (`a` inclusive but `b` exclusive.)

+ In iterator:

There are these symbols or keywords `..`, `..<` (`until`), `downTo`

These symbols or keywords can be used with `step` keyword.

Given these numbers `a`,`b`, and `x`.

- `..` : `a .. b` is equivalent to the iterator (an `IntRange` type) `(a,a+1,...b-1,,b)`. (both inclusive.) (in non-reversed order.)
- `..<` or `until` : `a..< b` is equivalent to the iterator (an `IntRange` type) `(a,a+1,...,b-1)`. (`a` inclusive but `b` exclusive.) (in non-reversed order.)
- `downTo` : `b downTo a` is equivalent to the iterator (an `IntRange` type) `(b,b-1,...,a+1,a)` (both inclusive.) (BUT in reversed order.)

| expression | inclusive or exclusive | non-reversed order or reversed order |
| :-- | :-- | :-- |
| `a .. b` | both inclusive. | non-reversed order |
| `a ..< b` or `a until b` | `a` inclusive but `b` exclusive. | non-reversed order |
| `b downTo a`| both inclusive. | reversed order |

+ Example 1:
  
| a | b | expression | returned iterator |
| :- | :- | :---------- | :----------------- |
| `3` | `7` | `3..7` | `(3,4,5,6,7)` | 
| `3` | `7` | `3..<7` or `3 until 7` | `(3,4,5,6)` | 
| `3` | `7` | `7 downTo 3` | `(7,6,5,4,3)` | 

It can be also used with `step`. The number after `step` keyword refers the number will be added to next element from current element.

+ Example 2:
  
| a | b | step | expression | returned iterator |
| :- | :- | :---------- | :----------------- | :----- |
| `3` | `7` | `2` | `3 .. 7 step 2` | `(3,5,7)` | 
| `3` | `7` | `2` | `3 ..< 7 step 2` or `3 until 7 step 2` | `(3,5)` | 
| `3` | `7` | `-2` | `7 downTo 3 step -2` | `(7,5,3)` | 

+ Example 3:

| a | b | step | expression | returned iterator |
| :- | :- | :---------- | :----------------- | :----- |
| `3` | `10` | `2` | `3 .. 10 step 2` | `(3,5,7,9)` | 
| `3` | `10` | `2` | `3 ..< 10 step 2` or `3 until 10 step 2` | `(3,5,7,9)` | 
| `3` | `10` | `-2` | `10 downTo 3 step -2` | `(10,8,6,4)` | 

For example, see `CH9 - range` in my example code[^1].

### data type
#### List type
It is often used when the order of elem is important.

##### `List`

> [!IMPORTANT]
> It is ***NOT*** mutable. That is, the element in `List` can NOT be changed.

###### construct
To construct a `List` with any elements (zero to any integer number of elements), one can use these methods
  + `listOf` (such as `listOf(1,2,3)`)

To construct `List` with zero element, use these methods.
  + `listOf` (through `listOf()`)
  + `emptyOf` (through `emptyOf()`)

###### API reference
For more details about `List`, see [`List` (Kotlin official docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list.html)

##### `MutableList`

> [!IMPORTANT]
> It is mutable. That is, the element in `MutableList` can be changed.

###### construct
To construct `MutableList` with any element, use these methods.
  + `mutableListOf` (through `mutableListOf(1,2,3)`)

To construct `MutableList` with zero element, use these methods.
  + `mutableListOf` (through `mutableListOf()`)

> [!IMPORTANT]
> `MutableList` is a subclass of `List`.

###### API reference
For more details about `MutableList`, see [`MutableList` (Kotlin official docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list.html)

#### Map type
To use the feature key-value pair, one can use Map.

##### `Map`

> [!IMPORTANT]
> It is ***NOT*** mutable. That is, the element in `Map` can NOT be changed.

###### construct
To construct `Map` with any element, use these methods.
  + `mapOf` (such as `mapOf( 'A' to 65 , 'B' to 66)`)

To construct `Map` with zero element, use these methods.
  + `mapOf` (through `mapOf()`)
  + `emptyMap()` (through `emptyMap()`)

###### API reference
For more details about `Map`, see [`Map` (Kotlin official docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/)

##### `MutableMap`

> [!IMPORTANT]
> It is mutable. That is, the element in `MutableMap` can be changed.

###### construct
To construct `MutableMap` with any element, use these methods.
  + `mutableMapOf` (such as `mapOf( 'A' to 65 , 'B' to 66)`)

To construct `MutableMap` with zero element, use these methods.
  + `mutableMapOf` (through `mutableMapOf()`)

> [!IMPORTANT]
> `MutableMap` is a subclass of `Map`.

###### API reference
For more details about `MutableMap`, see [`MutableMap` (Kotlin official docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/#kotlin.collections.MutableMap)

#### Set type
In math, there are unique value in a Set. And so in Kotlin.

If one think the uniqueness is important, use set Type.

##### `Set`

> [!IMPORTANT]
> It is ***NOT*** mutable. That is, the element in `Set` can NOT be changed.

###### construct
To construct `Set` with any element, use these methods.
  + `setOf` (such as `setOf( 'A','B')`)

To construct `Set` with zero element, use these methods.
  + `setOf` (through `setOf()`)
  + `emptySet` (through `emptySet()`)

###### API reference
For more details about `Set`, see [`Set` (Kotlin official docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-set/)

##### `MutableSet`

> [!IMPORTANT]
> It is mutable. That is, the element in `MutableSet` can be changed.

###### construct
To construct `MutableSet` with any element, use these methods.
  + `mutableSetOf` (such as `mutableSetOf( 'A','B')`)

To construct `MutableSet` with zero element, use these methods.
  + `mutableSetOf` (through `mutableSetOf()`)

> [!IMPORTANT]
> `MutableSet` is a subclass of `Set`.

###### API reference
For more details about `MutableSet`, see [`MutableSet` (Kotlin official docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-set/)

### null safety check
#### nullable check ?.

If the left hand side of `nullable check` (`?.` symbol) `<leftValue>` is NOT `null`, then the method or the property `<propertyNameOrMethodName>` will be evaluated then returned.

Otherwise, it will return `null`

```
<lvalue> = <leftValue>?.<propertyNameOrMethodName>
```

It is an abbreviation for

```
<lvalue> = if(<leftValue> == null) null else <rightValue>
```

For example, see `nullable check` in my example code[^1].

> [!CAUTION]
> It is NOT allowed to add space between these symbols.

### operation for List type

Common operations of List type

| operation for List type | inplace function | non-inplace function |
| :- | :- | :- |
| sort by ascending | `sort()` | `sorted()` |
| sort by descending | `sortDescending()` | `sortedDescending()` |
| reverse | `reverse()` | `reversed()`| 

> [!IMPORTANT]
> ***reverse v.s. reversed v.s. asReversed***
>
> `reverse` is an inplaced function, it will reverse the elements in the original object.
>
> `reversed` is a non-inplaced function, it will reverse the elements BUT return a new object. The original object does NOT be affected.
>
> `asReversed` is  non-inplaced function, it will return a reversed read-only view of the original object, thus all changes made in the original object will be reflected in the reversed one.

#### operation for `Collections`

> [!IMPORTANT]
> `List`, `Map`, `Set` are subclass of `Collections`
> 
| property | description |
| :- | :- |
| `size` | get the number of elements. | 

| methods | description |
| :- | :- |
| `count` | return the number of elements of orignal collection that satisfies the given predicate. If the predicate is NOT given, then default predicate is {`true`} which will return the number of elements in the original collection. | 

| methods | description |
| :- | :- |
| `contains` | return true iff the original collection contains the given element. | 
| `containsAll` | return true iff the original collection contains the given collection. |

| methods | description |
| :- | :- |
| `add` | add one element | 
| `addAll` | add one list into original collection. |

| methods | description |
| :- | :- |
| `remove` | remove the given element | 
| `removeAt` |  remove a corresponding element with given index |

| methods | description |
| :- | :- |
| `retainAll` | only retain the new collection | 

| methods | description |
| :- | :- |
| `clear` | clear the original collection | 

#### Elvis operator ?:

If the left hand of `Elvis operator` (`?:` symbol) `<leftValue>` is NOT `null`, then it will return the value `<leftValue>`.

Otherwise (i.e. the left hand of `Elvis operator` (`?:` symbol) `<leftValue>` is `null`), then it will evaluate the right hand side of `Elvis operator` `<rightValue>` and return the result.

```
<lvalue> = <leftValue> ?: <rightValue>
```

It is an abbreviation for

```
<lvalue> = if(<leftValue> == null) <leftValue> else <rightValue>
```

For example, see `Elvis Operator` in my example code[^1].

> [!CAUTION]
> It is NOT allowed to add space between these symbols.

#### non-null assertion operator !!

If the left hand side of `non-null assertion operator` (`!!` symbol) is NOT null, then the right hand side of `non-null assertion operator` will be evaluated and returned.

Otherwise, it will throw a NPE (NullPointerException).

```
if(<leftValue> == null) {
  throw NullPointerException(...)
} else {
  <lvalue> = <rightValue>
}
```

For example, see `non-null assertion operator` in my example code[^1].

> [!CAUTION]
> It is NOT allowed to add space between these symbols.

> [!CAUTION]
> Compare with the symbols.
>
> One can easily found the fact that
> 
> the left hand side of the symbols in `nullable check`, `Elvis operator` and `non-null assertion operator` must be an expression `<leftValue>` .
>
> On the other hand, the right hand side of `<rightValue>` in `Elvis operator` and `non-null assertion operator` must be an expression `<expression>`
>
> While that in `nullable check` must be a property or method `<propertyNameOrMethodName>`

### Regex
Regex[^2][^3][^4] in Kotlin is a class that handles string with re (regular expression) in Kotlin.

> [!TIP]
> The rule of re in Kotlin use that in JavaScript.

> [!TIP]
> The rule of re in Kotlin is quite similar to those in all languages.

> [!TIP]
> Here, I recommend a useful tool to handle text with re. regexr.com[^3].
>
> For more introduction about regexr.com[^3], see my notes at Github[^5].

### scope function
#### comparison

| Function | Object reference | Return value| Is extension function|
| :-- | :-- | :-- | :-- |
| [`let`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/let.html)| `it`| Lambda result| Yes |
| [`run`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/run.html) | `this`| Lambda result | Yes|
| [`run`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/run.html)|  \- | Lambda result | No: called without the context object|
| [`with`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/with.html)|`this`| Lambda result|No: takes the context object as an argument.|
| [`apply`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/apply.html)| `this`| Context object| Yes|
| [`also`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/also.html)| `it`| Context object|Yes|

#### recommend intention

Here is a short guide for choosing scope functions depending on the intended purpose:
- Executing a lambda on non-nullable objects: `let`    
- Introducing an expression as a variable in local scope: `let`
- Object configuration: `apply`
- Object configuration and computing the result: `run`
- Running statements where an expression is required: non-extension `run`
- Additional effects: `also`
- Grouping function calls on an object: `with`

#### footnote

[^1]: [Example code zip file](https://github.com/40843245/Kotlin_Tutorial/blob/main/Kotlin/example%20code/example%20code%20in%20Kotlin.7z)

[^2]: [Regex (Kotlin in TibMe)](https://kuroclass.gitbook.io/kotlin/v/ch9#matches)

[^3]: [a website of an regular expression](https://regexr.com/)

[^4]: [Regex (Kotlin API docs)](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/-regex/)

[^5]: [regexr (my notes at Github)](https://github.com/40843245/tool/blob/main/Data%20Processing/Text%20Processing/regular%20expression/regexr.com.md)
