---
layout: page
title: "Q190249: INFO: VB 6.0 Readme Part 9: DHTML Page Designer Issues"
permalink: /kb/190/Q190249/
---

## Q190249: INFO: VB 6.0 Readme Part 9: DHTML Page Designer Issues

{% raw %}

	Article: Q190249
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbhtml kbActiveX kbDHTML kbInternet kbPageDesigner kbVBp kbVBp600
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The information below includes the documentation and workarounds for Visual
	Basic 6.0. This information can also be found in the README.htm file that ships
	with Visual Basic 6.0 on the Visual Basic 6.0 CD-ROM. Please see the REFERENCES
	section of this article for a list of the Microsoft Knowledge Base articles
	relating to the Visual Basic 6.0 readme.
	
	Following is a list of all parts of the readme file:
	
	Part 1.  Important Issues - Please Read First!
	Part 2.  Data Access Issues and DataBinding Tips
	Part 3.  Control Issues
	Part 4.  Language Issues
	Part 5.  Samples Issues
	Part 6.  Wizard Issues
	Part 7.  Error Message Issues
	Part 8.  WebClass Designer Issues
	Part 9.  DHTML Page Designer Issues
	Part 10. Extensibility issues
	Part 11. Miscellaneous Issues
	Part 12. Microsoft Transaction Server (MTS) Issues
	Part 13. Dictionary Object
	Part 14. Visual Component Manager
	Part 15. Application Performance Manager
	
	MORE INFORMATION
	================
	
	DHTML Page Designer Issues
	--------------------------
	
	Page Designer Error Messages
	----------------------------
	
	There are currently no Help topics for the following error messages:
	
	- "Save internal HTML to File?"
	
	This occurs if you specify a new, existing HTML file in the Property Page.
	
	If you have HTML code in an instance of the Page Designer and you decide to
	use a different, existing HTML file with the designer, you must open the
	property page and specify the name of the existing file. The Page Designer
	must then know what to do with the internal HTML that is currently in the
	designer. If you answer Yes to this question, Visual Basic will save the
	HTML to a file after you specify a filename.
	
	- "DHTML Page Designers cannot be private"
	
	This occurs if you attempt to change a DHTML Page Designer's Public
	property to False. While ActiveX designers can be either public or private,
	they must be Public to be accessible in a DHTML application. Private
	designers can be useful in certain cases, such as in the Data Environment
	when you want to encapsulate your data access logic in the Data
	Environment, but not make it public.
	
	- "Reload changed HTML file?"
	
	This occurs if the Page Designer notices that the HTML file referenced by
	the designer has changed on disk. This message confirms whether you want to
	load the modified HTML back into the designer.
	
	Page Designer: "Me." Not Supported
	----------------------------------
	
	You cannot use the "Me" reference in your page designer code to reference
	the DHTMLPage object. For example, the documentation frequently shows that
	you can write code such as "Me.Document.item". This is not supported.
	Instead of using Me, you must use the "DHTMLPage" statement. For example,
	instead of Me.Document, you would use DHTMLPage.Document. If the designer
	is private, "Me" can be used, but private is not allowed in DHTML pages.
	
	Page Designer: Cannot Access HTML Elements from Forms or External Objects
	-------------------------------------------------------------------------
	
	You cannot write code in a form, message box, or other object that
	references HTML elements on the page. Page elements are only accessible
	within the page itself.
	
	Page Designer: Image SourceFiles are Resolved Incorrectly
	---------------------------------------------------------
	
	Often, as you work in the page designer, you will want to reference an
	image that is located in the same directory as your current HTML page.
	Normally, when you reference such an image, you do not include a path in
	the image element's SRC attribute. The lack of a path tells the browser to
	pull the image from the page's current directory. For example, you might
	enter "myimage.gif" in the SRC property for an image of this type, rather
	than specifying "c:\mydhtml\myimage.gif." This is called a relative path,
	because it does not specify the full location of the image file.
	
	At design-time, the page designer does not correctly display these images
	with relative paths. When you enter such a property value in the SRC
	property or display a page that contains such a reference, two things will
	happen:
	
	- The image element will appear empty at design time.
	
	- The page designer appends the word "About:" to the value of your SRC
	  property. For example, you might see "About:myimage.gif."
	
	Despite these problems, the image appears correctly when you run the
	project. So you can ignore the "About:" keyword that appears in the SRC
	property and the fact that the image doesn't appear in the designer. When
	you save the HTML file, the image tag will be written correctly.
	
	Page Designer: Binary Persistence Issue:
	
	Some controls attempt to save some or all of their properties in a binary
	format that cannot be directly represented in HTML. Because of this
	situation, some control properties may not be saved after you run your
	project. In order to correct this problem, set the property at run-time.
	The following list shows the known properties for which this problem
	occurs:
	
	  Tabbed Dialog Control: TabsPerRow property does not persist
	  Windowless Controls Listbox: List items do not persist
	  Common Controls: Tabstrip settings do not persist
	  Common Controls: Toolbar settings do not persist
	  Common Controls: StatusBar settings do not persist
	  ADODC Control: ConnectionString property does not persist
	
	In addition, for many controls, font properties do not persist. This
	occurrence is the most common manifestation of the binary persistence
	problem.
	
	Page Designer:
	Type Library Problems are Preventing Some Help Topics from Appearing
	--------------------------------------------------------------------
	
	When you begin a page designer project, you will see two DHTML type
	libraries in the Object Browser, the DHTMLPAGELIB library, and a
	DHTMLProject library.
	
	Help is enabled for the DHTMLPAGELIB library, but not for the DHTMLProject
	library. Most elements in DHTMLProject should be available within the other
	library. In other cases, type library problems are preventing certain
	pieces of the help to appear or function correctly. This happens in the
	following cases:
	
	- When you try to access help from the Properties window for an ActiveX
	  control's properties.
	
	- When you try to access help from the Code Editor window, for the
	  Document property.
	
	In most cases, you should be able to locate the topic you want through the
	index in the MSDN Help viewer.
	
	Page Designer: Modal Prompts Appear Behind Browser in Run Mode
	--------------------------------------------------------------
	
	If you add a message box to your DHTML page, the message box appears behind
	Internet Explorer when activated in run mode. In addition, you cannot move
	Internet Explorer out of the way in order to view the message, because the
	message is modal. When you hear the beep that indicates a message is on the
	screen, select the Visual Basic application from your taskbar to view and
	clear the message.
	
	Page Designer: Do Not Watch Objects of Type HTMLDocument
	--------------------------------------------------------
	
	Expanding a watch on objects of type HTMLDocument may cause problems within
	the IDE. Avoid watching objects of this type.
	
	Page Designer: Cannot Design Frames Within A Page Designer
	----------------------------------------------------------
	
	When you create Web pages in the DHTML Page Designer, you cannot insert
	framesets within the page and fill their contents. You can, however,
	display the pages you create for your DHTML application within a frameset
	created outside of Visual Basic. If you want to design and debug frames,
	the process is as follows:
	
	1. In Visual Basic, design the contents of each frame with an individual
	  DHTML Page Designer.
	
	2. In an external editing program, design the frameset document as a
	  separate .htm file and save it in the temp directory. Set the SRC
	  attributes for each frame to point to your content pages, using the
	  names you defined in their BuildFile properties.
	
	3. In Visual Basic, choose "Start Browser with URL" on the Debugging tab of
	  the Project Properties dialog box and enter the path of the frameset
	  file.
	
	4. Enter run mode. Visual Basic launches Internet Explorer and loads the
	  frameset page you designed in an external program. The frameset document
	  should then load your page designer pages in the appropriate frames.
	
	5. Debug your application as usual.
	
	Page Designer: Cannot use Visual Basic Code with the SetInterval Method
	-----------------------------------------------------------------------
	
	If you use the SetInterval method of the Internet Explorer BaseWindow
	object on a timer within your DHTML applications, you must set the first
	parameter of the method to point to a Javascript or VBScript time routine
	contained within the HTML page. This method cannot reference a Visual Basic
	routine within your page designer code.
	
	Page Designer: Control Issues
	-----------------------------
	
	The following are items to be aware of as you work with ActiveX Controls in
	your DHTML applications:
	
	- You must use the compiled version of any ActiveX controls you add to
	  your DHTML pages.
	
	- You cannot use a DHTML page within an ActiveX Control project in this
	  release. The reverse is also true -- that is, the ActiveX control
	  project cannot be part of the project group in which you are working.
	  The safest and most reliable way to build and debug a user control is to
	  compile the user control project, then close that project, add the
	  control to the page designer, and proceed from there. Interactive
	  debugging and design between the two projects is not possible at this
	  point.
	
	- When you embed an ActiveX control on a page in your DHTML application,
	  not all of the appropriate type library information is copied with it.
	  This can cause errors when you try to access a link in the object
	  browser to the information for that control, and it can prevent you from
	  accessing extended properties and methods for the control in the
	  statement completion window that appears when you write code.
	
	- Some ActiveX controls will not work correctly with the page designer.
	  You cannot use the following controls in a DHTML page: MS Chart, Script
	  Debugger, Hierarchical FlexGrid, SrcEdit OC, LayoutDTC, Tabular Data
	  control, PageNavbarDTC, DBGrid(use DataGrid that ships with VB6) or IE
	  Popup Window. In addition, you cannot use private or uncompiled user
	  controls on pages in your DHTML applications. In addition, it is
	  possible that some controls you have obtained from third parties may not
	  work correctly with the page designer.
	
	Most controls that work with Internet Explorer 4 should work with the page
	designer. If you buy a third-party control that does not work with the page
	designer, test it within Internet Explorer and then contact the control
	vendor. For information on how to build ActiveX controls that work with the
	page designer and Internet Explorer, please see the article "Building
	ActiveX Controls for Internet Explorer 4.0," available in your MSDN library
	or on Microsoft's Web site in the MSDN Online section.
	
	- If you have an ActiveX control for which you have set the background
	  transparent, it will appear opaque at design time when added to your
	  DHTML application.
	
	- If your DHTML page contains a Listview control and you try to access the
	  ColHeader.Width property, you will encounter an error saying that the
	  object does not support this property. The property does appear on the
	  Auto List Members drop-down list, but you should not use it in your
	  code.
	
	- Some Visual Basic controls, such as the common dialog or the sysinfo
	  control, are invisible at run-time. If you add one of these objects to
	  your HTML page, you cannot select it and move it around within the page
	  after you initially draw it. You can, however, select the control in the
	  treeview and either delete it or access its properties.
	
	- If you add a File Upload control (FlUpl) to your DHTML designer and you
	  click it during design-time, it will activate and display the standard
	  file chooser dialog box. You can cancel this dialog box and move on.
	
	- There is a nonfunctional InnerText property available in the Auto List
	  Members drop-down list for the horizontal rule element. Do not set a
	  value for this property as it will produce no result.
	
	- When you add an ActiveX control to your page, the Height and Width
	  properties do not update automatically as the control is resized in the
	  designer. To refresh the numbers in the height and width properties,
	  click in a blank area of the treeview after resizing your control.
	
	- When you click a control in the toolbox and then move the cursor to the
	  Design pane of the designer, the cursor does not change from an I-beam
	  to a pointer to indicate that you can click and draw your control. You
	  can still click and drag your control to the desired shape, even though
	  the cursor is still an I-beam.
	
	- When you copy controls between two DHTML projects in the same project
	  group, the Components dialog box is not updated. You will need to set
	  the necessary references to that control manually.
	
	- If you use the ImageList control, its picture will not be loaded if the
	  project is Run in debug mode. However, the image will work correctly
	  when you run the compiled DLL.
	
	Page Designer: Miscellaneous HTML Issues
	----------------------------------------
	
	The following are items to be aware of as you create and work with HTML in
	the DHTML page designer:
	
	- If your page contains a CHARSET metatag, this tag will be stripped out
	  when the page is read into the designer. This should not cause a problem
	  in most pages.
	
	- The column widths you see in tables within the designer may not match
	  the column widths you see when you run your page in the browser. You may
	  be able to avoid this problem either by setting your column widths in
	  percentages rather than pixels, or by making sure the left-most column
	  does not have a width measurement set for it.
	
	- Do not assign ID property values with greater than 117 characters. If
	  you do, you may receive an error when running your application.
	
	- If the first paragraph element on your page does not contain text and is
	  followed by another HTML element, you may see unexpected results if you
	  delete the first <P> tag. In this case, other elements on the page may
	  also be deleted.
	
	- You may receive inconsistent results when trying to delete a DIV tag
	  using the designer's treeview panel. If you have trouble deleting a DIV
	  tag, use the Launch Editor function and remove the <DIV> and </DIV> tags
	  manually.
	
	- When you run your project, table borders will appear only for cells that
	  contain text. You can force a table border to appear for empty cells in
	  your tables by placing a <BR> tag in each unused table cell.
	
	- Property values set for the TITLE element on your HTML page may not
	  persist in the property grid after you run the project. However, if you
	  examine the HTML source code in the browser you will see that your title
	  properties are still present in the HTML stream.
	
	- Elements on a page are always anchored by the upper left corner.
	  Therefore, if you resize the element by stretching the top or left
	  borders, you will see an element of the size you indicated when you
	  release the cursor but it will still be positioned from the original
	  top, left corner. This may produce unexpected results. You can avoid
	  this by first positioning your control with the upper left corner in the
	  appropriate place, then sizing it correctly.
	
	- You may have difficulty removing font formatting from some elements. For
	  example, if you add an H1 heading to your page, press ENTER, and type a
	  few sentences below it, the paragraph will receive the same formatting
	  as the heading, it will appear large and in bold. You cannot remove this
	  formatting using the bold icons on the formatting toolbar. You can
	  remove this kind of incorrect formatting either by using the Launch
	  Editor feature and manually correcting the formatting tags, or by
	  changing the style of the selected text in the designer to Normal.
	
	- Some properties that appear in the Properties window for the Document
	  object are not valid. These properties begin with the letters "on". If
	  you set a value for any of these properties, you will see no results
	  based on the value you set when you run the project or examine the HTML
	  source.
	
	- For a check box HTML element, a property called "Indeterminate" is used
	  to set the check box to a grayed-out state. However, if you set this
	  property to True and then click the check box to move it to the blank
	  state, the Indeterminate property does not reset to False. You can reset
	  it manually or click a third time to reset the value.
	
	- For absolutely positioned controls with Height and Width properties that
	  appear in the Properties window, you cannot resize the control by
	  changing the values of those properties directly. Instead, resize the
	  control by dragging one of its borders in the designer.
	
	- If you insert an input image element onto your page from the HTML
	  toolbox, then use the Shape property to change it from another shape to
	  a polygon, you will receive an error.
	
	- The treeview pane of the designer may not reflect the exact order of
	  items as they appear in the design pane. The treeview shows the
	  structural relationship of elements on the page in the order in which
	  they appear in the HTML stream. The position of an element in the HTML
	  stream does not always correspond to the position of an element on the
	  displayed page, because you can change an element's position with
	  attributes and inline styles. Your page will appear in Internet Explorer
	  as it does in the design pane of the designer.
	
	Page Designer: Miscellaneous Debugging Issues
	---------------------------------------------
	
	The following are items to be aware of as you debug and test your DHTML
	applications:
	
	- In the Locals window, functions used in your DHTML application are
	  listed twice. This may cause difficulty because it allows you to
	  seemingly set two different values for Booleans.
	
	- Several properties listed in the Locals window will produce an error if
	  you try to edit their value. These include the following properties:
	
	  DHTMLPage.BaseWindow.document.activeElement.all.length
	  DHTMLPage.BaseWindow.document.activeElement.offsetParent.all.length
	  DHTMLPage.BaseWindow.document.activeElement.children.length
	
	- If you refresh Internet Explorer while your DHTML project is in break
	  mode, then you return to run mode in Visual Basic, your breakpoints will
	  no longer be hit and stop instructions will no longer be followed. Stop
	  debug mode, then press the F5 key again to begin your debug process a
	  second time.
	
	Page Designer: Syntax for Navigating Programmatically
	-----------------------------------------------------
	
	In the "Navigating in DHTML Applications" topic in the Developing DHTML
	Applications section of the Building Internet Applications book, the
	documentation states that you can programmatically move between pages by
	using this syntax in your code:
	
	  Private Function Button1_onclick() As Boolean
	     BaseWindow.navigate "Project1.DHTMLPage2.html"
	  End Function
	
	This syntax is incorrect because an underscore rather than a period should
	separate the project name and the page name. The correct syntax to use is
	shown below:
	
	  Private Function Button1_onclick() As Boolean
	     BaseWindow.navigate "Project1_DHTMLPage2.html"
	  End Function
	
	Page Designer: OBJECT Tag Insertion
	-----------------------------------
	
	In the topic "Testing your DHTML Projects," the documentation states that
	an OBJECT tag is inserted into your page during debugging but does not
	state that this tag is enclosed in a METADATA tag that is also inserted at
	this time. In addition, the following clarifications may be helpful:
	
	- The contents of the OBJECT tag's CODEBASE attribute are filled in during
	  packaging, when you use the Package and Deployment Wizard to prepare
	  your project for distribution.
	
	- During debugging, the OBJECT tag is actually inserted into a temporary
	  copy of the HTML file. The final tag is set up during the packaging
	  process.
	
	Page Designer:
	Cannot CTRL+TAB Through Windows When Page Designer Has Focus
	------------------------------------------------------------
	
	When the Page Designer window has focus, you cannot use the CTRL+TAB
	keystroke to move through all open windows in the Visual Basic IDE as you
	can with other projects.
	
	Page Designer: Cannot Delete a Table if it Contains No Columns
	--------------------------------------------------------------
	
	If you delete all of the columns from a table on your page and then try to
	delete the table, it will still appear in the treeview pane of the
	designer. To delete the table from the treeview, you must delete the
	paragraph element under which the table element appears.
	
	Page Designer: When Using Visual SourceSafe with Page Designer Projects,
	You Must Manually Check in the Project's .HTM Files
	---------------------------------------------------
	
	When you check a DHTML project into Visual SourceSafe, the HTML pages
	associated with the project are not automatically checked into the
	SourceSafe tree with the rest of the project files. You must manually add
	them to the tree as related files.
	
	NOTE: This applies only when you have saved your HTML pages to external
	files. If you have saved them within the project there are no .htm files to
	check in for your design-time project.
	
	Page Designer:
	Unqualified BuildFile Property Results in DLL Building To Desktop
	-----------------------------------------------------------------
	
	If you edit the BuildFile property so that it does not specify the drive
	and directory in which the file should be placed, the system will build the
	resulting files directly to your desktop. Always enter the fully-qualified
	path when entering values for this property.
	
	Page Designer: Use of Load Event With Asynchronous Property
	-----------------------------------------------------------
	
	In the "Load Event" topic within the Reference section of the Visual Basic
	documentation in MSDN, the documentation incorrectly states the following:
	
	"Programmers can use this event when running asynchronously (when the
	AsyncLoad property is set to True) as a notification that all elements have
	been loaded onto the page."
	
	In fact, this should say that programmers can use the Load event when
	running synchronously (when AsyncLoad is set to False) as a notification
	that all elements have been loaded.
	
	Page Designer: Property Page Issues
	-----------------------------------
	
	The following are items to be aware of as you work in the property pages
	for various HTML elements in the DHTML Page Designer:
	
	- Some elements have additional tabs in their property pages that do not
	  appear when you view the property page in a DHTML project. In many
	  cases you can get to these tabs even if they are not visible by pressing
	  the TAB key.
	
	- If you make changes to the custom property page for an ActiveX control
	  you have added to your DHTML application, you may not always see those
	  changes reflected in your DHTML project. To correct this problem, close
	  your DHTML project and recompile the ActiveX control project. Your
	  changes should then appear in the DHTML project. Repeat this process
	  each time you make changes to the property page for the control.
	
	- The word "Test" will appear in the body of some property pages. This
	  will not cause any problems in your application.
	
	Page Designer: Location of Project Files in .CAB Deployment
	-----------------------------------------------------------
	
	In the topic "Deploying your DHTML Projects," the documentation states that
	the project DLL file, the Visual Basic run-time, and the .dsr and .dsx
	files for the project are all placed into the same .cab file during the
	deployment process. This is not correct. In fact, the .dsr and .dsx files
	for the project are not placed into the .cab.
	
	Page Designer: Name of Save Option Changed
	------------------------------------------
	
	In the documentation for the page designer, the procedures for choosing
	save options tell you to select a Page Properties dialog box option called
	"Save HTML Within the Designer" if you do not want to save to an external
	HTML file. This option is actually named "Save HTML as part of the VB
	Project."
	
	Page Designer:
	Problems Seeing Code Changes When Switching from Compiled to Debug Mode
	-----------------------------------------------------------------------
	
	You may, on occasion, encounter a problem where you do not see changes you
	have made to the code in your DHTML application when you have run the
	compiled DLL, made a change to the code, then entered debug mode. In this
	situation, you can try either of the following fixes:
	
	- Clear the Use Existing Browser check box on the Debugging tab of the
	  Project Properties dialog before you start the debug process, after
	  making changes to your code.
	
	- Exit the browser after running the compiled DLL, before opening the IDE
	  to make code changes.
	
	Page Designer: BuildFile Property and HTML File Created
	-------------------------------------------------------
	
	By default, the BuildFile property is set to the value of the SourceFile
	property. The SourceFile Property is null if you selected "Save HTML inside
	the VB Project" in the .DHTMLPage Properties dialog box, so in turn the
	BuildFile property is null by default. Selecting "Save HTML in an external
	file" in the .DHTMLPage Properties dialog box will set the SourceFile
	Property which in turn will set the BuildFile property. Just make sure you
	set the BuildFile property and always enter a fully qualified path.
	
	NOTE: You want to store your page as an external HTML file. The DHTML Page
	designer has some limitations when it comes to editing your HTML page. If
	you don't store your page as an external HTML file you will not be able to
	use an external editor on this page.
	
	Page Designer:
	Help on Most Language Elements Is Available in the Platform SDK
	---------------------------------------------------------------
	
	Most language elements in the page designer are inherited from the Internet
	Explorer's document object model. F1 for these elements is not available.
	To get help on these topics, open the "Platform SDK" node in the MSDN table
	of contents, then open the "Internet/Intranet/Extranet Services" node and
	look for the Dynamic HTML section. You can also use the Index to do a
	search for the name of a particular language element.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q170164 INFO: VB 6.0 Readme Part 1: Important Issues - Read First!
	
	  Q170163 INFO: VB 6.0 Readme Part 2: Data Access/Databinding Issues
	
	  Q170162 INFO: VB 6.0 Readme Part 3: Control Issues
	
	  Q170161 INFO: VB 6.0 Readme Part 4: Language Issues
	
	  Q170160 INFO: VB 6.0 Readme Part 5: Samples Issues
	
	  Q190046 INFO: VB 6.0 Readme Part 6: Wizard Issues
	
	  Q170158 INFO: VB 6.0 Readme Part 7: Error Message Issues
	
	  Q189539 INFO: VB 6.0 Readme Part 8: WebClass Designer Issues
	
	  Q170154 INFO: VB 6.0 Readme Part 10: Extensibility Issues
	
	  Q170157 INFO: VB 6.0 Readme Part 11: Miscellaneous Issues
	
	  Q170156 INFO: VB 6.0 Readme Part 12: Transaction Server (MTS) Issues
	
	  Q191792 INFO: VB 6.0 Readme Part 13: Dictionary Object
	
	  Q191791 INFO: VB 6.0 Readme Part 14: Visual Component Manager
	
	  Q191790 INFO: VB 6.0 Readme Part 15: Application Performance Explorer
	
	  Q190256 HOWTO: Show Table Borders for All Cells in DHTML Page Designer
	
	  Q190255 BUG: DHTML Page Designer Does Not Insert the <HTML> Tag
	
	  Q190254 BUG: Cannot Insert MFC 4.1-Based Controls in DHTML Page Designer
	
	  Q190251 BUG: Option Explicit Statement Is Not Added by a DHTML File
	
	  Q190250 BUG: DHTML Page Designer Cannot Find the Mshtml.hlp File
	
	  Q191183 HOWTO: Navigate Between DHTML Designer Pages
	
	Additional query words:
	
	======================================================================
	Keywords          : kbhtml kbActiveX kbDHTML kbInternet kbPageDesigner kbVBp kbVBp600 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
