---
layout: page
title: "Q110308: HOWTO: Encrypt a String with Password Security"
permalink: /kb/110/Q110308/
---

## Q110308: HOWTO: Encrypt a String with Password Security

{% raw %}

	Article: Q110308
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0 5.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbcode kbVBp400 kbVBp500 kbhowto
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	It is sometimes desirable to restrict the visibility of string constants within
	a Microsoft Visual Basic compiled application. In many cases, string constants
	remain in a linear, unencrypted form that debug/editor utilities can display.
	
	The sample Visual Basic code below encrypts a string with the XOR operator using
	password security. You can also adapt this technique to other dialects of Basic
	or other languages.
	
	NOTE: This behavior is not exhibited when a Visual Basic 5.0 application is
	compiled using the native mode compiler.
	
	MORE INFORMATION
	================
	
	Software tools for debugging and viewing binary code can easily find ASCII
	strings stored in compiled executable .EXE programs. If you want to hide or
	protect strings in .EXE programs, you can use techniques such as these:
	
	- Append a series of Chr$() functions in your Basic code. For example, the
	  following string concatenates ASCII values 65 through 68, which represent the
	  capital letters A through D:
	
	        A$ = Chr$(65) + Chr$(66) + Chr$(67) + Chr$(68)
	        Print A$
	
	  This code prints ABCD. Because the ABCD is stored in code instead of in a
	  string constant, it is not directly visible when viewed in a debugger. This
	  method is okay for small amounts of data, but is inefficient for larger
	  strings.
	
	- Add or subtract a constant or a letter's position value to the ASCII/ANSI
	  value of each character in the string.
	
	  NOTE: Don't exceed the byte value range of 0 to 255. For example, if you add
	  50 to the extended-ASCII character CHR$(230) and assign it to a string in
	  Basic, you get an "Illegal function call" error.
	
	- Use the Xor function in a formula using a key or password string. Byte values
	  changed with Xor always stay within the byte value range 0 to 255. This
	  technique is flexible and elegant. See the sample program in the next section
	  below.
	
	  NOTE: The Xor function is also known as the exclusive-OR function. An
	  exclusive-OR means A or B, but not both. For example, if A is true, and B is
	  false, then A Xor B is true, but if both A and B are true, then A Xor B is
	  false.
	
	- Use third-party compression and encryption software, such as LZEXE or PKLITE,
	  on the compiled executable EXE file. For secure encryption routines, see the
	  QuickPak Professional Library from Crescent Division, Progress Software,
	  Inc., shown in the Reference section below.
	
	- Keep a checksum to protect against viruses or hackers. You can keep a
	  checksum of various important values in the program, and the program can
	  refuse to run if any checksums have changed.
	
	  NOTE: A checksum is an error-detection scheme that involves creating a sum of
	  the bits in a set of bytes of data, then using that sum to later check for a
	  change in the data.
	
	Example of String Encryption Using Xor Function
	-----------------------------------------------
	
	Calling the Encrypt routine below encrypts a string using a password. Calling the
	Encrypt routine a second time decrypts the encrypted string.
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Add the following code to the Form Load event:
	
	     Sub Form_Load ()
	        form1.Show  ' Must Show form in Load event before Print is visible.
	        secret$ = "This is the string that will be encrypted."
	        PassWord$ = "password"
	
	        Call Encrypt(secret$, PassWord$)     'Encrypt the string.
	        Print " After encrypting it once: "  'Print the result.
	        Print secret$
	        Print
	
	        Call Encrypt(secret$, PassWord$)     'A second call to the Encrypt
	        Print "After a second encryption:"   'subroutine now decrypts the
	        Print secret$                        'encrypted string.
	
	     End Sub
	
	3. Add the following Encrypt procedure to the general declarations section:
	
	     Sub Encrypt (secret$, PassWord$)
	        ' secret$ = the string you wish to encrypt or decrypt.
	        ' PassWord$ = the password with which to encrypt the string.
	        L = Len(PassWord$)
	        For X = 1 To Len(secret$)
	           Char = Asc(Mid$(PassWord$, (X Mod L) - L * ((X Mod L) = 0), 1))
	           Mid$(secret$, X, 1) = Chr$(Asc(Mid$(secret$, X, 1)) Xor Char)
	        Next
	     End Sub
	
	4. Start the program, or press the F5 key. Close the form to end the program.
	
	Xor: The Exclusive-OR Operator
	------------------------------
	
	The exclusive-OR operator (Xor in the Basic language) performs a logical
	exclusion on two expressions. For example:
	
	     Result = expr1 Xor expr2
	
	A useful behavior of Xor is that the first expression expr1 is returned without
	losing any bits when you perform Result Xor expr2. This ability to restore the
	first expression from the Result combined with the second expression is why the
	Xor function is useful for encryption.
	
	The Xor operator performs a bit-wise comparison of identically positioned bits in
	two numeric expressions and sets the corresponding bit in the result according
	to the following truth table:
	
	  If bit in expr1 is:     And bit in expr2 is:    The result is:
	  ---------------------------------------------------------------
	        0                           0                    0
	        0                           1                    1
	        1                           0                    1
	        1                           1                    0
	
	ASCII and ANSI Character Sets
	-----------------------------
	
	For a listing of the ASCII and ANSI character sets, see the Help menu in Visual
	Basic.
	
	American Standard Code for Information Interchange (ASCII) is the 7-bit character
	set widely used to represent letters and symbols found on a standard United
	States keyboard. The ASCII character set is the same as the first 128 characters
	(0 to 127) in the American National Standards Institute (ANSI) character set.
	The ANSI character set uses all 8 bits in a byte, and includes 256 characters (0
	to 255). ANSI characters 128 to 255 are sometimes referred to as the
	extended-ASCII characters.
	
	REFERENCES
	==========
	
	The following company offers encryption software and other products for Basic:
	
	Crescent Division, Progress Software, Inc.
	14 Oak Park
	Bedford, MA 01730 USA
	Contact: Sales Information (800)352-2742, or
	Adam Schwartz (617)280-3000
	Fax: (617) 280-4025
	Internet Web Site http://www.crescent.progress.com
	Ask about the QuickPak Professional Library for Windows.
	
	Products from Progress Software are manufactured independent of Microsoft.
	Microsoft makes no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	======================================================================
	Keywords          : kb3rdparty kbcode kbVBp400 kbVBp500 kbhowto 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbVB400Search kbVB400 kbZNotKeyword3 kbVB16bitSearch
	Version           : 4.0 5.0
	
	=============================================================================
	

{% endraw %}
