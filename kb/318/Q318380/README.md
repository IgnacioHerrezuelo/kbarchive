---
layout: page
title: "Q318380: IIS Status Codes"
permalink: /kb/318/Q318380/
---

## Q318380: IIS Status Codes

{% raw %}

	Article: Q318380
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When users try to access content on your Internet Information Server (IIS) 4.0
	or Internet Information Services (IIS) 5.0 server through HTTP or File Transfer
	Protocol (FTP), IIS returns a numeric code that indicates the status of the
	request. This status code is recorded in the IIS log, and it may also be
	displayed in the Web browser or FTP client. The status code can indicate whether
	a particular request is successful or unsuccessful and can also reveal the exact
	reason why a request is unsuccessful.
	
	MORE INFORMATION
	================
	
	Log File Locations:
	
	By default, IIS places its log files in %WINDIR\System32\Logfiles. This directory
	contains separate directories for each World Wide Web (WWW) and FTP site. By
	default, logs are created in the directories daily and are named with the date
	(for example, exYYMMDD.log). For additional information about setting up
	logging, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q313437 HOW TO: Enable Logging in IIS 5.0
	
	HTTP:
	
	1xx - Informational
	
	These status codes indicate a provisional response. The client should be prepared
	to receive one or more 1xx responses before receiving a regular response.
	
	- 100 - Continue.
	
	- 101 - Switching Protocols.
	
	2xx - Success
	
	This class of status codes indicates that the server successfully accepted the
	client request.
	
	- 200 - OK. The client request has succeeded.
	
	- 201 - Created.
	
	- 202 - Accepted.
	
	- 203 - Non-Authoritative Information.
	
	- 204 - No Content.
	
	- 205 - Reset Content.
	
	- 206 - Partial Content.
	
	3xx - Redirection
	
	The client browser must take more action to fulfill the request. For example, the
	browser may have to request a different page on the server or repeat the request
	by using a proxy server.
	
	- 300 - Multiple choices.
	
	- 301 - Moved Permanently.
	
	- 302 - Found.
	
	- 303 - See Other.
	
	- 304 - Not Modified.
	
	- 305 - Use Proxy.
	
	- 306 - This code is reserved but not used.
	
	- 307 - Temporary Redirect.
	
	4xx - Client Error
	
	An error occurs, and the client appears to be at fault. For example, the client
	may request a page that does not exist, or the client may not provide valid
	authentication information.
	
	- 400 - Bad Request.
	
	- 401 - Access denied.
	
	IIS defines a number of different 401 errors that indicate a more specific cause
	of the error. These specific error codes are displayed in the browser but are
	not displayed in the IIS log:
	
	   - 401.1 - Logon failed.
	
	   - 401.2 - Logon failed due to server configuration.
	
	   - 401.3 - Unauthorized due to ACL on resource.
	
	   - 401.4 - Authorization failed by filter.
	
	   - 401.5 - Authorization failed by ISAPI/CGI application.
	
	- 403 - Forbidden.
	
	IIS defines a number of different 403 errors that indicate a more specific cause
	of the error:
	
	   - 403.1 - Execute access forbidden.
	
	   - 403.2 - Read access forbidden.
	
	   - 403.3 - Write access forbidden.
	
	   - 403.4 - SSL required.
	
	   - 403.5 - SSL 128 required.
	
	   - 403.6 - IP address rejected.
	
	   - 403.7 - Client certificate required.
	
	   - 403.8 - Site access denied.
	
	   - 403.9 - Too many users.
	
	   - 403.10 - Invalid configuration.
	
	   - 403.11 - Password change.
	
	   - 403.12 - Mapper denied access.
	
	   - 403.13 - Client certificate revoked.
	
	   - 403.14 - Directory listing denied.
	
	   - 403.15 - Client Access Licenses exceeded.
	
	   - 403.16 - Client certificate untrusted or invalid.
	
	   - 403.17 - Client certificate has expired or is not yet valid.
	
	- 404 - Not found.
	
	- 404.1 - Site not found.
	
	- 405 - Method not allowed.
	
	- 406 - Not acceptable.
	
	- 407 - Proxy authentication required.
	
	- 412 - Precondition failed.
	
	- 414 - Request-URI too long.
	
	5xx - Server Error
	
	The server cannot complete the request because it encounters an error.
	
	- 500 - Internal server error.
	
	- 500.12 - Application restarting.
	
	- 500.13 - Server too busy.
	
	- 500.15 - Requests for GLOBAL.ASA not allowed.
	
	- 500-100.ASP - ASP error (note that this code occurs with IIS 5.0 only).
	
	- 501 - Not implemented.
	
	- 502 - Bad gateway.
	
	- 503 - Service unavailable.
	
	- 504 - Gateway timeout.
	
	- 505 - HTTP version not supported.
	
	Common HTTP Status Codes and Their Causes:
	
	- 200 - Success. This status code indicates that IIS has successfully processed
	  the request.
	
	- 304 - Not Modified. The client requests a document that is already in its
	  cache and the document has not been modified since it was cached. The client
	  uses the cached copy of the document, instead of downloading it from the
	  server.
	
	- 401.1 - Logon failed. The logon attempt is unsuccessful, probably because of
	  a user name or password that is not valid.
	
	- 401.3 - Unauthorized due to ACL on resource. This indicates a problem with
	  NTFS permissions. This error may occur even if the permissions are correct
	  for the file that you are trying to access. For example, you see this error
	  if the IUSR account does not have access to the C:\Winnt\System32\Inetsrv
	  directory.
	
	For additional information about how to resolve this problem, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q187506 List of NTFS Permissions Required for IIS Site to Work
	
	- 403.1 - Execute access forbidden. The following are two common causes of this
	  error message:
	
	   - You do not have enough Execute permissions. For example, you may receive
	     this error message if you try to access an ASP page in a directory where
	     permissions are set to None, or you try to execute a Common Gateway
	     Interface (CGI) script in a directory with Scripts Only permissions. To
	     modify the Execute permissions, right-click the directory in the Microsoft
	     Management Console (MMC), click Properties, click the Directory tab, and
	     make sure that the Execute Permissions setting is appropriate for the
	     content that you are trying to access.
	
	   - The script mapping for the file type that you are trying to execute is not
	     set up to recognize the verb that you are using (for example, GET or
	     POST). To verify this, right-click the directory in the MMC, click
	     Properties, click the Directory tab, click Configuration, and verify that
	     the script mapping for the appropriate file type is set up to allow the
	     verb that you are using.
	
	- 403.2 - Read access forbidden. Verify that you have set up IIS to allow Read
	  access to the directory. Also, if you are using a default document, verify
	  that the document exists.
	
	For additional information about how to resolve this problem, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q247677 Error Message: 403.2 Forbidden: Read Access Forbidden
	
	- 403.3 - Write access forbidden. Verify that the IIS permissions and the NTFS
	  permissions are set up to grant Write access to the directory.
	
	For additional information about how to resolve this problem, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q248072 Error Message: 403.3 Forbidden: Write Access Forbidden
	
	- 403.4 - SSL required. Disable the Require secure channel option, or use HTTPS
	  instead of HTTP to access the page.
	
	If you receive this error for a Web site that does not have a certificate
	installed, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q224389 Err Msg: HTTP Error 403, 403.4, 403.5 Forbidden: SSL Required
	
	- 403.5 - SSL 128 required. Disable the Require 128-bit encryption option, or
	  use a browser that supports 128-bit encryption to view the page.
	
	If you receive this error for a Web site that does not have a certificate
	installed, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q224389 Err Msg: HTTP Error 403, 403.4, 403.5 Forbidden: SSL Required
	
	- 403.6 - IP address rejected. You have configured your server to deny access
	  to your current IP address.
	
	For additional information about how to resolve this problem, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q248043 Error Message: 403.6 - Forbidden: IP Address Rejected
	
	- 403.7 - Client certificate required. You have configured your server to
	  require a certificate for client authentication, but you do not have a valid
	  client certificate installed.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q190004 Error 403.7 or 'Connection to Server Could Not Be Established'
	
	
	- 403.8 - Site access denied. You have set up a domain name restriction for the
	  domain that you are using to access your server.
	
	For additional information about how to resolve this problem, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q248032 Error Message: Forbidden: Site Access Denied 403.8
	
	- 403.9 - Too many users. The number of users who are connected to the server
	  exceeds the connection limit that you have set. For additional information
	  about how to change this limit, click the article number below to view the
	  article in the Microsoft Knowledge Base:
	
	  Q248074 Error Message: Access Forbidden: Too Many Users Are Connected 403.9
	
	  NOTE: Microsoft Windows 2000 Professional and Microsoft Windows XP
	  Professional automatically impose a 10-connection limit on IIS. You cannot
	  change this limit.
	
	- 403.12 - Mapper denied access. The page that you want to access requires a
	  client certificate, but the user ID that is mapped to your client certificate
	  has been denied access to the file.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q248075 Error: HTTP 403.12 - Access Forbidden: Mapper Denied Access
	
	- 404 - Not found. This error may occur if the file that you are trying to
	  access has been moved or deleted. It can also occur if you try to access a
	  file that has a restricted file name extension after you install the URLScan
	  tool. In this case, you see "Rejected by URLScan" in the log file entry for
	  that request.
	
	- 500 - Internal server error. You see this error message for a wide variety of
	  server-side errors. Your event viewer logs may contain more information about
	  why this error occurs. Additionally, you can disable friendly HTTP error
	  messages to receive a detailed description of the error.
	
	For additional information about how to disable friendly HTTP error messages,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q294807 HOWTO: Disable Internet Explorer 5 'Show Friendly HTTP Error
	  Messages' Feature on the Server Side
	
	- 500.12 - Application restarting. This indicates that you tried to load an ASP
	  page while IIS was in the process of restarting the application. This message
	  should disappear when you refresh the page. If you refresh the page and the
	  message appears again, it may be caused by antivirus software that is
	  scanning your Global.asa file.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q248013 Err Msg: HTTP Error 500-12 Application Restarting
	
	- 500-100.ASP - ASP error. You receive this error message when you try to load
	  an ASP page that has errors in the code. To obtain more specific information
	  about the error, disable friendly HTTP error messages. By default, this error
	  is only enabled on the default Web site.
	
	For additional information about how to see this error on non-default Web sites,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q261200 HTTP 500 Error Message Displays Instead of ASP Error Message from
	  500-100.asp
	
	- 502 - Bad gateway. You receive this error message when you try to run a CGI
	  script that does not return a valid set of HTTP headers.
	
	FTP:
	
	1xx - Positive Preliminary Reply
	
	These status codes indicate that an action has started successfully, but the
	client expects another reply before it continues with a new command.
	
	- 110 Restart marker reply.
	
	- 120 Service ready in <nnn> minutes.
	
	- 125 Data connection already open; transfer starting.
	
	- 150 File status okay; about to open data connection.
	
	2xx - Positive Completion Reply
	
	An action has successfully completed. The client can execute a new command.
	
	- 200 Command okay.
	
	- 202 Command not implemented, superfluous at this site.
	
	- 211 System status, or system help reply.
	
	- 212 Directory status.
	
	- 213 File status.
	
	- 214 Help message.
	
	- 215 NAME system type, where NAME is an official system name from the list in
	  the Assigned Numbers document.
	
	- 220 Service ready for new user.
	
	- 221 Service closing control connection. Logged out if appropriate.
	
	- 225 Data connection open; no transfer in progress.
	
	- 226 Closing data connection. Requested file action successful (for example,
	  file transfer or file abort).
	
	- 227 Entering Passive Mode (h1,h2,h3,h4,p1,p2).
	
	- 230 User logged in, proceed.
	
	- 250 Requested file action okay, completed.
	
	- 257 "PATHNAME" created.
	
	3xx - Positive Intermediate Reply
	
	The command was successful, but the server needs additional information from the
	client to complete processing the request.
	
	- 331 User name okay, need password.
	
	- 332 Need account for login.
	
	- 350 Requested file action pending further information.
	
	4xx - Transient Negative Completion Reply
	
	The command was not successful, but the error is temporary. If the client retries
	the command, it may succeed.
	
	- 421 Service not available, closing control connection. This may be a reply to
	  any command if the service knows it must shut down.
	
	- 425 Can't open data connection.
	
	- 426 Connection closed; transfer aborted.
	
	- 450 Requested file action not taken. File unavailable (for example, file
	  busy).
	
	- 451 Requested action aborted: local error in processing.
	
	- 452 Requested action not taken. Insufficient storage space in system.
	
	5xx - Permanent Negative Completion Reply
	
	The command was not successful, and the error is permanent. If the client retries
	the command, it receives the same error.
	
	- 500 Syntax error, command unrecognized. This may include errors such as
	  command line too long.
	
	- 501 Syntax error in parameters or arguments.
	
	- 502 Command not implemented.
	
	- 503 Bad sequence of commands.
	
	- 504 Command not implemented for that parameter.
	
	- 530 Not logged in.
	
	- 532 Need account for storing files.
	
	- 550 Requested action not taken. File unavailable (for example, file not
	  found, no access).
	
	- 551 Requested action aborted: page type unknown.
	
	- 552 Requested file action aborted. Exceeded storage allocation (for current
	  directory or dataset).
	
	- 553 Requested action not taken. File name not allowed.
	
	Common FTP Status Codes and Their Causes:
	
	- 150 - FTP uses two ports: 21 for sending commands, and 20 for sending data. A
	  status code of 150 indicates that the server is about to open a new
	  connection on port 20 to send some data.
	
	- 226 - The command opens a data connection on port 20 to perform an action,
	  such as transferring a file. This action successfully completes, and the data
	  connection is closed.
	
	- 230 - This status code appears after the client sends the correct password.
	  It indicates that the user has successfully logged on.
	
	- 331 - You see this status code after the client sends a user name. This same
	  status code appears regardless of whether the user name that is provided is a
	  valid account on the system.
	
	- 426 - The command opens a data connection to perform an action, but that
	  action is canceled, and the data connection is closed.
	
	- 530 - This status code indicates that the user cannot log on because the user
	  name and password combination is not valid. If you use a user account to log
	  on, you may have mistyped the user name or password, or you may have chosen
	  to allow only Anonymous access. If you log on with the Anonymous account, you
	  may have configured IIS to deny Anonymous access.
	
	- 550 - The command is not executed because the specified file is not
	  available. For example, this status code occurs when you try to GET a file
	  that does not exist, or when you try to PUT a file in a directory for which
	  you do not have Write access.
	
	REFERENCES
	==========
	
	For more information about HTTP status code definitions, visit the following
	World Wide Web Consortium (W3C) Web site:
	
	  Status Code Definitions
	  http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10
	
	For more information about FTP status code definitions, view section 4.2 ("FTP
	Replies") at the following W3C Web site:
	
	  File Transfer Functions
	  http://www.w3.org/Protocols/rfc959/4_FileTransfer.html
	
	Additional query words: iis 5
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : :4.0,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
