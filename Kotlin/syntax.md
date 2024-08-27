# Kotlin
## syntax
### entry point

> [!CAUTION]
> In kotlin, each `.kt` must have an entry point.

> [!CAUTION]
> In kotlin, an entry point is a `main` function.
>
> ```
> fun main(){
>   <mainBody>
> }
> ```

### conditional statement

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

#### footnote

[^1] [Example code zip file](https://github.com/40843245/Kotlin_Tutorial/blob/main/Kotlin/example%20code/example%20code%20in%20Kotlin.7z)
