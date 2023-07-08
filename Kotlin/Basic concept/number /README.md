# Type of Number and Operation between them.
### Number 
All available numbers in Kotlin:

Integer:

      decimal
      hexdecimal
      binary number

Float:

      float
      double
      
#### Decimal Number
See my note in docx in Github. (for convenience to type formula)  
##### Conversion
1. Explicit conversion : Supported for all types.
2. Implicit conversion : Only supported for type of smaller number to bigger number, NOT supported for type pf bigger number to smaller number.

###### Explicit Conversion
For objects whose type in decimal numbers, there are these methods to<type>.

      toByte : to Byte. Its syntax is toByte()
      toShort : to Short. Its syntax is toShort()
      toInt : to Int. Its syntax is toInt()
      toLong : to Long. Its syntax is toLong()
      toFloat : to Float. Its syntax is toFloat()
      toDouble : to Double. Its syntax is toDouble()

###### Implicit Conversion
Only supported for type of smaller number to bigger number, NOT supported for type pf bigger number to smaller number.

The rules are following:

      1. If number x <= Max Value of Int , it will be cast to Int.

      2. If number x > Max Value of Int , it will be cast to Long.

## Operator
### Arithmetic Operatior
      + : plus

      - : minus

      * : multiplication

      / : division

            For x / y, when x and y are both Int, it will return Int

      % : modulus

#### Type of result after operation between two
Iff both of dividend and divisor are not Float and Double type, the fraction of result will be discarded.
i.e. Iff one of dividend and divisor are either Float or Double type, the fraction of result will NOT be discarded.

For the table, see the docx file.

https://github.com/40843245/Kotlin_Tutorial/tree/main/Kotlin/Basic%20concept/Type/docx

#### Overloading
Overloading of operator for numbers:
            
            + 
            - 
            / 
            * 
            %
            
Example of overloading of operator:

      val l = 1L + 3 // Long + Int => Long

### Bitwise Operator   

      shl : signed shift left.
      shr : signed shift right.
      ushr : unsigned shift right.
      and : bitwise and
      or : bitwise or
      xor : bitwise xor
      inv : bitwise inversion (i.e. bitwise not)

#### signed left shift 
I want to call left shift as zero-fill left shift.

The excess bit(s) from the left (before shiftness) will be discarded after shiftness.

It will fill 0 from right when shiftness.

##### Ref
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Left_shift

#### signed shift right
In signed shift right, the excess bit(s) from the right will be stored as the bit(s) to fill from left respectively.

For fully understand, I recommend you to calculate it with the following example.

##### Example
![image](https://github.com/40843245/Kotlin_Tutorial/assets/75050655/d1716884-352c-4768-bb4f-d32bb9f078e6)

The example is from the reply on the stackoverflow from the following link in Ref section.

##### Ref
https://stackoverflow.com/questions/7522346/right-shift-and-signed-integer

#### unsigned shift right
Unsigned shift right is also called zero-fill shift right.

The excess bit(s) from the right (before shiftness) will be discarded after shiftness. 

It will fill 0 from left when shiftness.

Thus, for unsigned number, the result of unsigned right shift will >= 0 .

##### Ref
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unsigned_right_shift

#### bitwise not
For each bit, 0 will be negated to 1 while 1 will be negated to 0.

### NOTICE
1. There does NOT exist ushl (unsigned shift left), for the reseason why, simply think about what is unsigned shift right.
      
## Comparison

       == : equal. It returns true iff the values of two numbers are equal.
       != : not equal. It is opposite of == .
       < : less than.
       > : greater than.
       <= : less than or equal to. Mixed of < and == .
       >= : greater than or equal to. Mixed of > and == . 
