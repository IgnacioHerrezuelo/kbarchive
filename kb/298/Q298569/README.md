---
layout: page
title: "Q298569: /Oxs Is Always Present in Project Options"
permalink: /kb/298/Q298569/
---

## Q298569: /Oxs Is Always Present in Project Options

{% raw %}

	Article: Q298569
	Product(s): Microsoft C Compiler
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kbtool kbui
	Last Modified: 28-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft eMbedded Visual C++, Version:3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you change the C/C++ Optimizations Project setting, the compiler flags may
	not be affected as you expect. Instead, /Oxs is always present in project
	options regardless of the optimization you select.
	
	CAUSE
	=====
	
	The settings database does not contain any optimizations other than /Oxs,
	maximum opts. and favor code space.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to systems
	that are experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information about support costs, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix has the following file attributes or later:
	
	  Date         Time        Size         File name
	  ------------------------------------------------
	  20-Jul-2001  22:27       1,290,301    Devbld.pkg
	  20-Jul-2001  16:29       2,134,016    Vccedb.mdb
	
	
	
	NOTE: The settings database was updated to use the following settings:
	
	  Default = /O2 maximize speed
	  Disable = /Od disable optimizations
	  minimize space = /Oxs maximum opts. and favor code space
	  maximize speed = /Oxt maximum opts. and favor code speed
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool kbui 
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
