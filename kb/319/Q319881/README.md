---
layout: page
title: "Q319881: XCON: How to Troubleshoot Exchange 5.5 Behind Proxy Server"
permalink: /kb/319/Q319881/
---

## Q319881: XCON: How to Troubleshoot Exchange 5.5 Behind Proxy Server

{% raw %}

	Article: Q319881
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may not be able to send outbound Internet e-mail or receive inbound Internet
	e-mail from behind a proxy server. This article explains how to troubleshoot
	Exchange Server 5.5 when it is used with Microsoft Proxy Server 2.0.
	
	RESOLUTION
	==========
	
	To troubleshoot e-mail flow issues from Exchange Server to Internet recipients
	from behind Proxy Server, follow these steps:
	
	
	1. Test e-mail flow from at least two different internal user accounts by
	  sending e-mail to at least two different e-mail domains. Can users send
	  e-mail to external Internet domains?
	
	   - NO. Continue.
	
	   - YES. If some users can send e-mail or if some domains can be sent to,
	     troubleshoot the server and its connectivity to the remote domains in
	     question before you continue to troubleshoot the Proxy Server computer. To
	     start troubleshooting, set up the SMTP Protocol Log, and then try to
	     telnet to the remote domain's e-mail server on port 25.
	
	  For additional information about how to do this, click the article numbers
	  below to view the articles in the Microsoft Knowledge Base:
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	  Q257538 XFOR: How to Obtain Additional Information from Internet Mail or
	  Unsolicited Commercial E-Mail
	
	  NOTE: Find out whether more than one Internet Mail Service exists.
	
	2. Do users receive non-delivery reports (NDRs) when they send e-mail to
	  Internet recipients, or do Internet originators receive an NDR when they send
	  e-mail to the Exchange Server users?
	
	   - NO. Continue.
	
	   - YES. Check the NDR for the reasons why they are being sent. (For example,
	     see whether the NDR includes "MSEXCH:IMS:Org:Site:Srvr Host unreachable"
	     or "MSEXCH:MTA:Org:Site:Srvr Unknown Recipient".)
	
	3. Are the messages remaining in the Exchange Server Internet Mail Service
	  Queues?
	
	   - NO. Continue.
	
	   - YES. View the details of the message.
	
	     Under Recipients, what reason is given? (For example, "Host Unreachable" or
	     "Network Error During Host Resolution".)
	
	4. Are all core Exchange Sever services and the Internet Mail Service started
	  without errors in the Application and System Log?
	
	   - NO. Search the Microsoft Knowledge Base for information about the errors.
	
	     NOTE: If the Internet Mail Service does not start properly, remove the
	     Proxy Client and Wspcfg.ini files from the server, and then try to start
	     the Internet Mail Service.
	
	     For additional information about how to do this, click the article number
	     below to view the article in the Microsoft Knowledge Base:
	
	  Q181847 XADM: How to Configure Exchange Server with Proxy Server
	
	     If the Internet Mail Service continues to fail, check the Application log
	     for errors.
	
	   - YES. Continue.
	
	5. Are the Exchange Server computer and proxy server and their respective
	  operating systems using the latest service packs?
	
	   - NO. Update both servers by using the latest service packs or builds
	     (hotfixes).
	
	   - YES. Continue.
	
	6. Is there antivirus software running on the Exchange Server computer?
	
	   - NO. Continue.
	
	   - YES. Temporarily turn off all antivirus software for troubleshooting.
	
	     NOTE: With some antivirus software, you may have to remove the antivirus
	     software completely before you continue.
	
	7. Does e-mail flow when you change the Internet Mail Service settings on the
	  Connections tab to "Forward all messages to host" instead of "Use domain name
	  system (DNS)" or vice versa? (To view the Connections tab, select the
	  appropriate Internet Mail Service in the Microsoft Exchange Administrator
	  program, and then click Properties on the File menu.)
	
	  For additional information, click the article number below to view the article
	  in the Microsoft Knowledge Base:
	
	  Q182339 XFOR: Verifying the Configuration of an Internet Mail Service
	
	   - NO. Continue.
	
	   - YES. This may not be a Proxy Server problem; it may be a common Internet
	     Mail Service issue. Do telnet tests and resolution tests to rule out
	     possible causes.
	
	8. Is there more than one network adapter network adapter or IP address
	  associated with the Exchange Server computer?
	
	   - NO. Continue.
	
	   - YES. Check the binding order of the network adapters. The internal network
	     adapter should be listed first using TCP/IP. Verify that the IP addresses
	     are correct and all settings match proper configuration (For example,
	     check the Subnet mask, gateway address, DNS, and WINS.)
	
	9. Is the Proxy client loaded and started on the Exchange Server computer?
	
	   - NO. Install the client.
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q181847 XADM: How to Configure Exchange Server with Proxy Server
	
	   - YES. Continue.
	
	10. Are the Wspcfg.ini files installed properly on the Exchange Server
	  computer?
	
	   - NO. Install the INI files.
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q181847 XADM: How to Configure Exchange Server with Proxy Server
	
	   - YES. Continue.
	
	11. Can the Exchange Server computer ping the proxy server by using the fully
	  qualified domain name (FQDN) of the proxy server or the IP address?
	
	   - NO. Network communication problems may exist. Troubleshoot connectivity
	     and resolution.
	
	   - YES. Continue.
	
	12. Log on to the Exchange Server computer. Can you telnet directly to the local
	  Exchange Server computer's IP address on port 25 and verify that the
	  Internet Mail Service answers? (Microsoft Exchange Internet Mail Service
	  5.5.26XX.XX)
	
	   - NO. Stop all other Simple Mail Transfer Protocol (SMTP) services on the
	     server, and then start the Internet Mail Service service.
	
	     NOTE: If Internet Mail Service is started, type "NETSTAT -anp tcp |more"
	     (without the quotation marks) at a command prompt on the Exchange Server
	     computer, and then verify that port 25 is listening. You should see the
	     following:
	
	     Proto Local Address Foreign Address State 
	     TCP 0.0.0.0:25 0.0.0.0:0 LISTENING
	
	     If port 25 is listening but not answering, restart the service or reinstall
	     the Internet Mail Service.
	
	   - YES. Continue.
	
	13. When you telnet to the local Exchange server on port 25, can you send
	  yourself a test message?
	
	  For additional information about using Telnet, click the article number below
	  to view the article in the Microsoft Knowledge Base:
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	   - NO. If you cannot send a test message, follow these steps:
	
	     a. Identify where that message is located.
	
	     b. Check the configuration of the Internet Mail Service.
	
	     c. Turn on Message Tracking and track the message.
	
	   - YES. Continue.
	
	14. At a command prompt on the proxy server, type " NETSTAT -ANP TCP |MORE"
	  (without the quotation marks), and then press ENTER
	
	  Is port 25 listening on the local address? You should see the following:
	
	  Proto Local Address Foreign Address State 
	  TCP 0.0.0.0:25 0.0.0.0:0 LISTENING
	
	   - NO. Check the Wspcfg.ini file and Proxy Client on the Exchange Server.
	     Restart Proxy, and then restart Exchange.
	
	   - YES. Continue.
	
	15. From an external client, can you telnet to the public IP address of the
	  Proxy Server on port 25 and verify that Exchange Server answers?
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	   - NO. If another service answers, identify and turn this service off. Try to
	     telnet from the Proxy Server to the external IP address on port 25. If
	     still no answer, go back to step 13.
	
	   - YES. Continue.
	
	16. From this telnet session to the public IP address of the proxy server on
	  port 25, can you send a test message to a user?
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	   - NO. Do you receive an NDR? Track the Message if you have to.
	
	   - YES. Continue.
	
	17. From the Exchange Server computer, can you telnet on port 25 to an external
	  e-mail server and send a test message?
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	   - NO. Try to telnet to another external e-mail server. If this fails, telnet
	     from the proxy server or from the external router to the external e-mail
	     server.
	
	   - YES. Continue.
	
	18. Are there any other servers or network components between the Exchange
	  Server computer, Proxy Server, and Internet?
	
	   - NO. Continue.
	
	   - YES. If possible, bypass these components, check configuration, or try to
	     telnet from these services to the internal or remote e-mail servers on
	     port 25.
	
	19. Does e-mail flow when you remove the Proxy Client from the Exchange Server
	  computer?
	
	   - NO. Reapply the client, and the Wspcfg.ini files. Restart the server, and
	     then continue troubleshooting.
	
	   - YES. Check the Proxy Server configuration or contact Microsoft Proxy
	     Support.
	
	20. Does the proxy server have a predefined filter for SMTP on the WinProxy
	  service?
	
	  (In Internet Service Manager, right-click the WinSock Proxy service, click
	  Properties, and then click Security to view the filter settings.)
	
	   - NO. Add this filter and Restart both Proxy and Exchange servers.
	
	   - YES. Continue.
	
	If you answered the preceding questions and found no problems at each step, you
	should have proper e-mail flow. If you still do not have good e-mail flow,
	either continue with the following options or contact Microsoft Support services
	(Exchange XCON or Proxy Services).
	
	Additional Exchange Server Troubleshooting Steps
	------------------------------------------------
	
	1. Remove the Proxy Client and the Internet Mail Service completely, and then
	  restart the server.
	
	2. Reinstall the Internet Mail Service (keep the default values) and the Proxy
	  Client.
	
	3. Reinstall the service packs for the operating system and for Exchange Server.
	
	4. Set the Exchange Server's Diagnostic Logging Category SMTP PROTOCOL LOG to
	  MAXIMUM and view any errors.
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q257538 XFOR: How to Obtain Additional Information from Internet Mail or
	  Unsolicited Commercial E-Mail
	
	  NOTE: This log is useful as long as e-mail is flowing in at least one
	  direction.
	
	Additional Proxy Server Troubleshooting Steps
	---------------------------------------------
	
	1. Reinstall the service packs for the operating system and for Microsoft Proxy
	  Server on the proxy server.
	
	2. Capture the network traffic by using Network Monitor and view for errors.
	
	  For additional information about how to do this, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q148942 How to Capture Network Traffic with Network Monitor
	
	For additional information about troubleshooting Exchange behind Proxy, click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q178532 XFOR: Configuring Exchange Internet Protocols with Proxy Server
	
	  Q181420 How to Configure Exchange or Other SMTP with Proxy Server
	
	  Q181847 XADM: How to Configure Exchange Server with Proxy Server
	
	  Q182339 XFOR: Verifying the Configuration of an Internet Mail Service
	
	  Q222553 XFOR: IMC Events 4020, 4007 with Error 10048: Winsock Failed to
	  Initialize
	
	  Q256145 Use Network Monitor to Determine Proxy Server Configuration
	
	  Q258022 Configure Proxy Server to Proxy Multiple Exchange Servers
	
	  Q276388 XIMS: How to Configure Exchange 2000 Behind Proxy Server 2.0
	
	
	Additional query words: front page
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword6 kbExchangeSearch kbExchange550 kbExchangeClientSearch kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
