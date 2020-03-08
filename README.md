# hp-41_SpreadSheet
Want to have a spreadsheet on your HP-41 calculator? Here's a way.

This program is an advancement of the spredsheet program "MicroCalc" created by Namir Shammas sometimes in the early 1980s (User program #01115C) - adding many features from the CX. It has the basic features you would expect from the usual spreadsheet programs (such as Excel) with any amount of calculations per cell that an HP-41 is capable of (an impressive lot) and the number of cells that you can fit into the calculator memory (in practical terms, a 100 cells).

Each "cell" is an HP-41 register, starting with Register 01. Reg 00 is used by the program to hold the name of the current worksheet and the current cell. A spreadsheet is created by adding a new program labeled simply from 0 to 9 as an Alpha label. The spreadsheet with "LBL '0" (LBL Alpaha 0 Alpha) must hold as many numeric lables as there are cells in the spreadsheet in addition to a LBL 00 that holds the number of columns and rows in the spreadheet. Like this:

```
LBL "0"
LBL 00
2
3
RTN
LBL 01
LBL 02
LBL 03
LBL 05
RTN
LBL 04
RCL 01
RCL 02
*
RTN
LBL 06
RCL 02
X^2
RCL 03
SIN
/
RCL 05
+
RTN
END
```

The above program is the definition of spreadsheet "0". 

The first number under LBL 00 is the number of columns, the second is the number of rows. The 6 cells are then distributed like this in the spreadsheet:

|Reg01 | Reg02
|Reg03 | Reg04
|Reg05 | Reg06

All the cells (labels) that are simple "input"-type cells (cells without any calculations) are grouped at the top (after LBL 00) and ends in a simple RTN (indicating no calculations for those cells). Cells that contain calculations (like LBL 04 and 06) contain the calculations as seen in the above example.

When you start the main program (XEQ "SHEET") you will be asked to enter the spreadsheet (a number from 0 to 9). You will then see the content of cell 1. Pressing R/S will show the mnemonics for the first row of User Defined Keys (keys A-E). Make sure you have USER pressed to get access to the User Defined Keys. Pressing R/S again shows the mnemonics for the shifted User Defined Keys (keys a-e). Pressing R/S again will get you back to showing the current cell's content. Any time the current cell content is shown, pressing R/S will show you the menu and another R/S will show the shifted menu. The mnemonics (in parenthesis) are:

Label (Menu)    | Description
----------------|------------
LBL A (#)		| Used for numeric input type cells: Input the cell number, then the numeric value and press A to store the value in that cell
LBL B (-)		| Go to one cell lower and show the content
LBL C (+R)      | Go to the cell in next row and show the content (stops at bottom row)
LBL D (+)		| Go to one cell higher and show the content
LBL E (V)		| View the content of the current cell (the cell number is in register Y)
----------------|------------
LBL a (A)		| Used for storing an Alpha value in a cell. Put up to 6 characters in Alpha, the cell number in X and press "a"
LBL b (1)		| Go to first cell and show the content
LBL c (-R)      | Go to the cell in higher row and show the content (stops at top row)
LBL d (E)		| Go to last cell and show the content
LBL e (S)		| Save the spreadsheet (all cells, including Reg 00) to an XM file named the same as the spreadsheet program (number from 0 to 9)

If you have a spreadsheet saved when you start the main program, it will automatically load the content of all the cells from that XM file.

To show the content of each consequtive cells, run the main program and press "D" and the program will advance one cell at a time and show the content (cell number is always left in register Y), doing calculations for the cells as directed.

