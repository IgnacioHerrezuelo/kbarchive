---
layout: page
title: "Q67031: C1001: '@(#)regMD.c:1.100', Line 3101"
permalink: /kb/067/Q67031/
---

## Q67031: C1001: '@(#)regMD.c:1.100', Line 3101

{% raw %}

	Article: Q67031
	Product(s): See article
	Version(s): 6.00 6.00a | 6.00 6.00a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a | mspl13_c
	Last Modified: 18-NOV-1990
	
	The sample code below produces the following internal compiler errors
	under different versions of the compiler when any of the following
	individual optimizations are used:
	
	   /Oa /Oc /Oi /On /Op /Or /Os /Ot /Ow /Oz
	
	Internal Compiler Error Under C 6.00a
	-------------------------------------
	
	test.c(11) : fatal error C1001: Internal Compiler Error
	                   (compiler file '@(#)regMD.c:1.100', line 3101)
	                   Contact Microsoft Product Support Services
	
	Internal Compiler Error Under C 6.00
	------------------------------------
	
	   test.c(11) : fatal error C1001: Internal Compiler Error
	                      (compiler file '@(#)regMD.c:1.100', line 3074)
	                      Contact Microsoft Product Support Services
	
	The following are three possible workarounds:
	
	1. Add one of the following optimizations:
	
	      /Od /Oe /Og /Ol /Ox
	
	2. Do not declare the structure variables of type register.
	
	3. Use an if-else statement instead of the ternary operator.
	
	Sample Code
	-----------
	
	1:  void main(void)
	2:  {
	3:     struct foo {
	4:           int i;
	5:     };
	6:     int n;
	7:
	8:     register struct foo *moo, *goo;
	9:
	10:    moo=goo;
	11:    n= moo->i ? moo->i :10000;
	12: }

{% endraw %}
