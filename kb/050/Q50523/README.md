---
layout: page
title: "Q50523: Floating-Point Initialization Occurs at Link Time"
permalink: /kb/050/Q50523/
---

## Q50523: Floating-Point Initialization Occurs at Link Time

{% raw %}

	Article: Q50523
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | S_QuickC S_QuickASM | mspl13_c
	Last Modified: 21-MAR-1990
	
	Floating-point initialization occurs at link time. If the compiler has
	generated any floating-point instructions, it lists an external
	symbol. When the linker sees the external symbol, it brings in the
	necessary segment.
	
	In C 5.10, the external symbol is __fltused. The linker brings in a
	module that has a common CDATA segment that defines the correct values
	of fpmath, fpdata, and fpsignal. If this module is not brought in, the
	CDATA segment defaults to all zeros. This is why CDATA is defined as
	common and not public.
	
	This process causes the floating-point support to be linked only if
	floating point is used.

{% endraw %}
