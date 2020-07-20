---
layout: post
title:  "Numerical Primitive Data Types In C#"
date:   2020-07-21 08:00:00
label: note
---

## Integrals

### byte

* Bits: 8 bits
* Ranges:
    * sbyte = -128 to 127
    * byte = 0 to 255

### short
* Bits: 16 bits
* Ranges:
    * short = -32,768 to 32,767
    * ushort = 0 to 65,535

### int
* Bits: 32 bits
* Ranges:
    * int = -2,147,483,648 to 2,147,483,647
    * uint = 0 to 4,294,967,295

### long
* Bits: 64 bits
* Ranges:
    * long = -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
    * ulong = 0 to 18,446,744,073,709,551,615

### char
* Bits: 16 bits
* Ranges:
    * letters
    * symbols
    * hex (i.e. \x0058)
    * unicode (i.e. \u0058)
* Use: Accepts 1 character

## Floating Points

### float
* Bits: 32 bits
* Range: -3.402823e38 to 3.402823e38
* Use:
    * Ended with an f (otherwise it will be assumed to be a double)
    * Accurate to 7 decimal units   

### double
* Bits: 64 bits
* Range: -1.79769313486232e308 to 1.79769313486232e308
* Use: Accurate to 15-16 decimal units
    
### decimal
* Bits: 128 bits
* Range: +/- (1.0x10^-28) to (7.9 x 10^28)
* Use:
    * Ended with an m (otherwise it will be assumed to be a double)
    * Accurate to 28-29 decimal units
    * Used to represent financial or monetary values