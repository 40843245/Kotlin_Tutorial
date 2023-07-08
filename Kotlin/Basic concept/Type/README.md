# Type 
## Number 
All available numbers in Kotlin:

Integer:

      decimal
      hexdecimal
      binary number

Float:

      float
      double
      
### Decimal Number
See my note in docx in Github. (for convenience to type formula)  
#### Conversion
1. Explicit conversion : Supported for all types.
2. Implicit conversion : Only supported for type of smaller number to bigger number, NOT supported for type pf bigger number to smaller number.

##### Explicit Conversion
For objects whose type in decimal numbers, there are these methods to<type>.

      toByte : to Byte. Its syntax is toByte()
      toShort : to Short. Its syntax is toShort()
      toInt : to Int. Its syntax is toInt()
      toLong : to Long. Its syntax is toLong()
      toFloat : to Float. Its syntax is toFloat()
      toDouble : to Double. Its syntax is toDouble()

##### Implicit Conversion
Only supported for type of smaller number to bigger number, NOT supported for type pf bigger number to smaller number.

The rules are following:

      1. If number x <= Max Value of Int , it will be cast to Int.

      2. If number x > Max Value of Int , it will be cast to Long.

   

