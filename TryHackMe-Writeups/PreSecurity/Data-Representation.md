# Inside a Computer System

## Overview

This room explains the Data Representation.

## What I Learned

If a computer were limited to 8 colors, it would only need to indicate which color is “switched on” and which is “switched off.” In fact, it can use three digits of 1 and 0 to represent the states of red, green, and blue. For example, 111 would be all 3 lights switched on, while 100 would be only the red switched on. This digit, which can be either 1 or 0, is called a bit.

**Color Representation 	    	Color Name**
000 	                 	    Black
001 	                 	    Blue
010 	                 	    Green
100 	                	    Red
011 	                	    Cyan
101 	                 	    Magenta
110 	                 	    Yellow
111 	                	    White

## Exercises

### Exercise 1 — [Representing Colors]

**Q1.** Preview the color #3BC81E. In one word, what does this color appear to be?
**Answer:** Green

**Q2.** What is the binary representation of the color #EB0037?
**Answer:** 11101011 00000000 00110111

**Q3.** What is the decimal representation of the color #D4D8DF?
**Answer:** 212 216 223

### Exercise 2 — [Numbers: Decimals to Hexadecimeal]

**Q1.** What is the hexadecimal FF in binary?
**Answer:** 1111 1111

**Q2.** What is the hexadecimal AB in decimal?
**Answer:** 171

**Q3.** Convert the hexadecimal FF FF FF to decimal. After you round up the decimal value to the nearest million, how many millions is that?
**Answer:** 17

## Key Takeaways

    Decimal (Base-10) system: This is the system we use in our everyday life.
    Binary (Base-2) system: Computers understand two states, which are encoded as 0 and 1.
    Hexadecimal (Base-16) system: Every 4 binary digits (bits) can be grouped as one hexadecimal digit. A hexadecimal digit ranges between 0 and F.
    Octal (Base-8) system: Every 3 binary digits (bits) can be grouped as one octal digit. An octal digit ranges between 0 and 7. This one is less commonly encountered on computer systems.

    Bit: It is short for binary digit, and it can be either 0 or 1.
    Byte: On modern systems, a byte is 8 bits. It is also referred to as an octet.
    Hex color: A color is represented as a combination of red, green, and blue on computer systems. If one byte is assigned for each of the primary colors (red, green, and blue), we can get more than 16 million color combinations.


## Notes

Converting an octal number to its decimal equivalent follows the steps of the previous conversions. Consider the octal number 357.
357 = 3 × 82 + 5 × 81 + 7 × 80 = 3 × 64 + 5 × 8 + 7 × 1 = 239

**Converting From Hexadecimal to Decimal System**
If you are curious about converting a hexadecimal number to a decimal number, you would follow the same approach we used for binary conversion. Let’s say that we want to convert the hexadecimal number 9B DF to decimal.
9BDF = 9 × 163 + 11 × 162 + 13 × 161 + 15 × 160 = 9 × 4096 + 11 × 256 + 13 × 16 + 15 × 1 = 39,903