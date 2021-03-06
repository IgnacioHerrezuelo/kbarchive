---
layout: page
title: "Q50698: CodeView 2.20 Does Not Allow Routine.Variable Specification"
permalink: /kb/050/Q50698/
---

## Q50698: CodeView 2.20 Does Not Allow Routine.Variable Specification

{% raw %}

	Article: Q50698
	Product(s): See article
	Version(s): 2.20   | 2.20
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | S_PASCAL S_C H_FORTRAN H_MASM DOCERR | mspl13_basic
	Last Modified: 10-NOV-1989
	
	On Pages 91-92 of the "CodeView and Utilities" manual that accompanied
	C 5.10 and Pascal 4.00 for CodeView Version 2.20, the period is
	documented as being useful as a specifier of local variables in parent
	functions. The syntax is stated to be as follows:
	
	   routine_name.variable_name
	
	However, this feature was not implemented in Version 2.20 of CodeView.
	It was implemented in CodeView Version 2.30 (which accompanied FORTRAN
	5.00).
	
	This feature is useful in all languages, but particularly helpful in
	Pascal because of the "nested-scoping" (the ability of a function to
	access variables from the routine that called it) that occurs in
	Pascal.
	
	To use this feature in CodeView 2.30, you must be in either the
	routine where the variable is defined or in a routine that is a child
	(or grandchild, etc.) of that routine. After entering the proper
	routine, any variable name can be referenced with a routine and
	variable name (see example below).
	
	program first (input, output) ;
	var a: integer ;            { Available throughout the program }
	
	    procedure second ;
	    var b: integer ;        { Available in second and third }
	
	        procedure third ;
	        var c: integer ;    { Available in third }
	
	        begin
	            a := 3 ;
	            b := 3 ;
	            c := 3 ;
	        end ;
	
	    begin
	        a := 2 ;
	        b := 2 ;
	        third ;
	    end ;
	
	begin
	    a := 1 ;                { Cannot watch second/third variables }
	    second ;
	end.
	
	When in procedure third, you can place a watch on the variables in
	procedure second in the following manner:
	
	w? second.b
	
	This will display the variable in procedure second. This variable
	cannot be displayed from the main program, however.

{% endraw %}
