---
layout: page
title: "Q32415: Cannot Use Alternate Math Library Without Compiling BC /FPa"
permalink: /kb/032/Q32415/
---

## Q32415: Cannot Use Alternate Math Library Without Compiling BC /FPa

{% raw %}

	Article: Q32415
	Product(s): See article
	Version(s): 6.00 6.00b 7.00 | 6.00 6.00b 7.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 2-FEB-1990
	
	The alternate math libraries should not be used without compiling with
	the BC /FPa switch; otherwise, unpredictable results may occur.
	
	The following alternate math libraries can be used in MS OS/2
	protected mode:
	
	   BC 6.00           BC 6.00b         PDS 7.00
	   -------           --------         --------
	
	   BRUN60AP.DLL      BRUN61AP.DLL     BRT70ANP.DLL
	   BCOM60AP.LIB      BCOM61AP.LIB     BRT70ANP.LIB
	                                      BRT70AFP.DLL
	                                      BRT70AFP.LIB
	
	The following alternate math libraries can be used in MS-DOS or MS
	OS/2 real mode:
	
	   BC 6.00           BC 6.00b         PDS 7.00
	   -------           --------         --------
	
	   BRUN60AR.EXE      BRUN61AP.EXE     BRT70ANR.EXE
	   BCOM60AR.LIB      BRUN61AP.LIB     BRT70ANR.LIB
	                                      BRT70AFR.EXE
	                                      BRT70AFR.LIB
	
	This information applies to Microsoft BASIC Compiler Versions 6.00 and
	6.00b for MS-DOS and MS OS/2 and to Microsoft BASIC Professional
	Development System (PDS) Version 7.00 for MS-DOS and MS OS/2.

{% endraw %}
