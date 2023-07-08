# Range instantiation
The following keyword and notation and combination of them can create a list of range.

    ..
    ..<
    step
    downto

## syntax
For convenience, we use re (regular expression) to represent the syntax.

    {rangeInstantiation} : {start}{spaces}{avaialble_keywords_or_notation}{spaces}{end}{spaces}{downto}+

    {spaces} : {space}*

    {space} : ' ' # one space
    
    {start} : {number}

    {end} : {number}

    {number} : [+|-]{digits}

    {digits} : {digit}*

    {digit} : [0-9]

    {avaialble_keywords_or_notation} :  {upto}|{downto}

    {downto} : "downto"
    
    {upto} : {upto_no_less} | {upto_less} 

    {upto_no_less} : ".."

    {up_to_less} : "..<"

### Recall
Recall about notation of re.

    {start}+ : refers {start} is matched 0 or 1 time.
    
    {a}|{b} : refers match either {a} or {b}.

## category 
1. From down to up, the value of end is greater than or equal to the value of start.

Such as

      [1,3,5,7,9]

or equivalent said 

      1 .. 9 step 2
    
2. From up to down, the value of end is less than the value of start.

Such as 

      [9,7,5,3,1] 

or equivalent said 

      9 downto 1 step 2

## ..
### intro
The expression 

    {start} .. {end}

will create a list with open-ended upward approach (i.e.from {start} to {end} (inclusively) ) 

With step (represented as identifier {step}) as default value -- 1.

### Example
#### Example 1
    
    3..9

will create a list

    [3,4,5,6,7,8,9]

## ..<
### intro
The expression 

    {start} ..< {end}

will create a list with close-ended upward approach (i.e.from {start} to {end} (exclusively) ) 

With step (represented as identifier {step}) as default value -- 1.

### Example
#### Example 1
    
    3..<9

will create a list

    [3,4,5,6,7,8]

## step
### intro 
The keyword step can set the step.

## downto
### intro
The keyword downto indicates to ount downward. It is commonly used when {end} < {start}.

