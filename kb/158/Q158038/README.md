---
layout: page
title: "Q158038: STL Sample for the stack::operation"
permalink: /kb/158/Q158038/
---

## Q158038: STL Sample for the stack::operation

{% raw %}

	Article: Q158038
	Product(s): Microsoft C Compiler
	Version(s): 4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbVC420 kbVC500 kbVC600 kbDSupport
	Last Modified: 17-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Standard C++ Library, used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The sample code below illustrates how to use the stack::operator< STL
	function in Visual C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	     <stack>
	
	Prototype
	---------
	
	     template<class _TYPE, class _C, class _A>
	     bool stack::operator<(const stack<_TYPE, _C, _A>& _X) const;
	
	NOTE: The class/parameter names in the prototype may not match the version in the
	header file. Some have been modified to improve readability.
	
	Description
	-----------
	
	The stack::operator< function returns true if the stack on the left side of
	the operator is less than the stack on the right side. The following steps are
	used to determine if one stack is less than another stack:
	
	1. Compare the bottom-most (very first element pushed onto the stack).
	
	2. If the elements are different, the stack with the smaller element is less
	  than the stack with the greater element. Go to Step 5.
	
	3. If the elements are the same and there are more elements, move to the next
	  element in the stack and go back to step 2.
	
	4. If all the elements in the stacks are processed at this point, the stacks are
	  equal.
	
	5. Done.
	
	Sample Code
	-----------
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: /GX
	  // 
	  // StackLessThan.cpp : Illustrates how to use the stack::operator<
	  //                     function to determine if one stack is less than
	  //                     another stack.
	  // 
	  // Functions:
	  // 
	  //    operator< :  Returns true if the stack is smaller than the stack
	  //                 passed as the operand.
	  // 
	  // Written by Derek Jamison
	  // of Microsoft Product Support Services,
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  #pragma warning(disable:4786)
	
	  #include <stack>
	  #include <iostream>
	  using namespace std;
	
	  #if _MSC_VER > 1020   // if VC++ version is > 4.2
	     using namespace std;  // std c++ libs implemented in std
	     #endif
	
	  typedef stack<double, deque<double, allocator<double> >,
	
	                allocator<double> > STACK_DOUBLE;
	
	  void main()
	
	  {
	
	     STACK_DOUBLE stack1,stack2;
	
	     // Add item 4.0 to Stack1. Stack1 contains 4.0.
	     cout << "stack1.push(4.0)  s1=[4.0]" << endl;
	     stack1.push(4.0);
	
	     // Add item 3.0 to Stack1. Stack1 contains 3.0(top) and 4.0(bottom).
	     cout << "stack1.push(3.0)  s1=[3.0 4.0]" << endl;
	     stack1.push(3.0);
	
	     // Add item 4.0 to Stack2. Stack2 contains 4.0 (top=bottom).
	     cout << "stack2.push(4.0)  s2=[4.0]" << endl;
	     stack2.push(4.0);
	
	     // Compare if Stack1 is smaller than Stack2. Should return False.
	     cout << "stack1<stack2 is " <<
	        ((stack1<stack2)? "True": "False") << endl << endl;
	
	     // Add item 6.0 to Stack2. Stack2 contains 6.0(top) and 4.0(bottom).
	     cout << "stack2.push(6.0)  s2=[6.0 4.0]" << endl;
	     stack2.push(6.0);
	
	     // Compare if Stack1 is smaller than Stack2. Should return True.
	     cout << "stack1<stack2 is " <<
	        ((stack1<stack2)? "True": "False") << endl << endl;
	
	     // Add item 8.0 to Stack2. Stack2 contains 8.0(top), 6.0 and
	     // 4.0(bottom).
	     cout << "stack2.push(8.0)  s2=[8.0 6.0 4.0]" << endl;
	     stack2.push(8.0);
	
	     // Compare if Stack1 is smaller than Stack2. Should return True.
	     cout << "stack1<stack2 is " <<
	        ((stack1,stack2)? "True": "False") << endl << endl;
	
	     // Delete item 8.0 from Stack2.
	     cout << "stack2.pop()      s2=[6.0 4.0]" << endl;
	     stack2.pop();
	
	     // Delete item 6.0 from Stack2.
	     cout << "stack2.pop()      s2=[4.0]" << endl;
	     stack2.pop();
	
	     // Add item 3.0 to Stack2. Stack2 contains 3.0(top) and 4.0(bottom).
	     cout << "stack2.push(3.0)  s2=[3.0 4.0]" << endl;
	     stack2.push(3.0);
	
	     // Compare if Stack1 is smaller than Stack2. Should return False.
	     cout << "stack1<stack2 is " <<
	        ((stack1<stack2)? "True": "False") << endl << endl;
	
	     // Delete item 3.0 from Stack2.
	     cout << "stack2.pop()      s2=[4.0]" << endl;
	     stack2.pop();
	
	     // Delete item 4.0 from Stack2.
	     cout << "stack2.pop()      s2=[]" << endl;
	     stack2.pop();
	
	     // Add item 8.0 to Stack2. Stack2 contains 8.0(top=bottom).
	     cout << "stack2.push(8.0)  s2=[8.0]" << endl;
	     stack2.push(8.0);
	
	     // Compare if Stack1 is smaller than Stack2. Should return True.
	     cout << "stack1<stack2 is " <<
	        ((stack1<stack2)? "True": "False") << endl << endl;
	
	  }
	
	Program Output is:
	
	  stack1.push(4.0)  s1=[4.0]
	  stack1.push(3.0)  s1=[3.0 4.0]
	  stack2.push(4.0)  s2=[4.0]
	  stack1<stack2 is False
	
	  stack2.push(6.0)  s2=[6.0 4.0]
	  stack1<stack2 is True
	
	  stack2.push(8.0)  s2=[8.0 6.0 4.0]
	  stack1<stack2 is True
	  <BR/><BR/>
	  stack2.pop()      s2=[6.0 4.0]
	  stack2.pop()      s2=[4.0]
	  stack2.push(3.0)  s2=[3.0 4.0]
	  stack1<stack2 is False
	
	  stack2.pop()      s2=[4.0]
	  stack2.pop()      s2=[]
	  stack2.push(8.0)  s2=[8.0]
	  stack1<stack2 is True
	
	REFERENCES
	==========
	
	Visual C++ Books On Line: Visual C++ Books:C/C++:Standard C++ Library Reference.
	
	Additional query words: STL STLSample operator
	
	======================================================================
	Keywords          : kbcode kbVC420 kbVC500 kbVC600 kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVCLibrary
	Version           : :4.2,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
