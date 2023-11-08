# AliExpress_8x8matrix
Alternate version of I2C LED Backpack library to deal with AliExpress 8x8 LED matrix with garbled display 

There are 8x8 LED I2C matrices being sold which give garbled display when you try to use them with standard libraries. This is probably a manufacturing error: X axis is off by one (1..7,0 in stead of 0..7), Y axis row 2 and 4 are swapped and axis is upside down.

This library fixes those errors by introducing a new matrix object: AliExpress_8x8matrix

Fixes are:
```
// fix Ali* error #1 - X is off by 1
x = x + 1;

// fix Ali* error #2 - Y row 2 and 4 are swapped and rows are upside down
if ((y==2) || (y==4)) {
  y = 6-y;
}
y = 7-y;
```
I put this example and library here for anyone else wondering why their matrix is showing garbage.
