---
layout: page
title: "Q60786: DOSCALLS.LIB Is Not Shipped with C 6.00"
permalink: /kb/060/Q60786/
---

## Q60786: DOSCALLS.LIB Is Not Shipped with C 6.00

{% raw %}

	Article: Q60786
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 17-DEC-1990
	
	After installing Microsoft C Version 6.00, you may try and compile
	your program and link with DOSCALLS.LIB. This process worked correctly
	with C Version 5.10, but does not work with C Version 6.00. You will
	receive the following error:
	
	   L4051: doscalls.lib : cannot find library.
	
	It may appear as if something is wrong with your environment. In fact,
	there is no DOSCALLS.LIB supplied with C 6.00. Use OS2.LIB instead.
	OS2.LIB contains all the functionality of DOSCALLS.LIB in addition to
	having Presentation Manager (PM) support.

{% endraw %}
