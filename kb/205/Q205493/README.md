---
layout: page
title: "Q205493: FP: How to Use the META Element with Web Spiders and Robots"
permalink: /kb/205/Q205493/
---

## Q205493: FP: How to Use the META Element with Web Spiders and Robots

{% raw %}

	Article: Q205493
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 09-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 98 version of this article, see Q194310.
	
	For a Microsoft FrontPage 97 and earlier version of this article, see Q170555.
	
	SUMMARY
	=======
	
	Web spiders (also called robots) are a great resource for people searching the
	Internet, but they present a problem to Web page designers who want their pages
	to be seen and properly indexed. One popular solution to this behavior is to use
	the Hypertext Markup Language (HTML) META element.
	
	MORE INFORMATION
	================
	
	The META element is placed in the HEAD element to embed document
	meta-information that is not defined by other HEAD elements. This embedded
	information can be extracted by servers and clients to identify, index, and
	catalog specialized document meta-information.
	
	META elements are added to the HEAD section of an HTML document, and can be
	written in one of two forms: META NAME and META HTTP-EQUIV.
	
	- NAME elements are used to specify user variables, or variables that can be
	  used by a client, such as a Web spider.
	
	- HTTP-EQUIV elements are used to specify system variables and are treated as
	  part of the HTTP response header, which is normally sent by the Web server.
	
	These META elements resemble the following examples when viewed in HTML:
	
	  <META NAME="author" CONTENT="John Doe">
	  <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=windows-1252">
	
	The NAME or HTTP-EQUIV attribute declares a variable for the page and the CONTENT
	attribute assigns a value to the variable.
	
	A META element standard for web spiders has evolved, which consists of two
	elements:
	
	Description    A brief description of the Web page.
	
	Keywords       One or more words that refer to the content on a Web page. 
	
	NOTE: Some web spiders ignore the Description attribute and use their own
	algorithm to generate a description of the page.
	
	Two examples using this standard are as follows:
	
	- Example 1:
	
	  <META NAME="description" CONTENT="Web spider information">
	  <META NAME="keywords" CONTENT="robots, spiders">
	
	- Example 2:
	
	  <META NAME="description" CONTENT="The Jogging Page">
	  <META NAME="keywords" CONTENT="jogging, health, fitness">
	
	To add a META tag similar to these examples on your Web page, follow these
	steps:
	
	1. Open a Web page in FrontPage.
	
	2. On the File menu, click Properties.
	
	3. In the Page Properties dialog box, click the Custom tab.
	
	4. In the User Variables section, click Add.
	
	5. In the Name box, type the name of the META variable. For example, type
	  "description" (without the quotation marks).
	
	6. In the Value box, type the contents of the META variable. For example, type
	  "This is my web page" (without the quotation marks).
	
	7. Click OK to add the variable.
	
	8. Click OK to exit the Page Properties dialog box.
	
	9. Save the page to your Web.
	
	REFERENCES
	==========
	
	For additional information about working with Web spiders and robots, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q217103 How to Write a Robots.txt File
	
	Additional query words: kbhowto front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbZNotKeyword5
	Version           : :
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
