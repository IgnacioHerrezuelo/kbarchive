---
layout: page
title: "Q286196: IISReset May Not Save IIS Configuration Changes"
permalink: /kb/286/Q286196/
---

## Q286196: IISReset May Not Save IIS Configuration Changes

{% raw %}

	Article: Q286196
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you make changes to your Internet Information Services (IIS) configuration
	through the Microsoft Management Console (MMC) or through scripting, some
	changes may not be saved after you use the iisreset command from the MMC or from
	a command prompt with no switches.
	
	CAUSE
	=====
	
	The IISReset command line tool waits for a normal shutdown of the services
	before it starts them again. Because of the number of services that are
	dependent on the IISAdmin service, the shutdown may not occur in a timely
	manner. When this happens, IISReset forces the shutdown of the services. This
	can result in metabase changes that are not saved properly.
	
	WORKAROUND
	==========
	
	To save the IIS configuration to the metabase, use the net stop and the net
	start commands to stop and start your services, or stop and start the services
	from the MMC snap-in. To locate the snap-in, follow these steps:
	
	1. On the task bar click Start, point to Programs, point to Administrative
	  Tools, and then click Services.
	
	2. Right-click IISAdmin Service and click Stop.
	
	The following examples illustrate the commands that are necessary to stop and
	start IIS from a command prompt. To stop IIS from a command prompt:
	
	  net stop iisadmin /y
	
	NOTE: Take note of each of the services that depend on the IISAdmin Service,
	because you need to restart each of these services in the next step.
	
	To start IIS from a command prompt:
	
	  net start w3svc
	  net start msftpsvc
	  net start smtpsvc
	  net start <short name for any other services that are listed when you stop IIS>
	
	NOTE: Because W3SVC and the other services that are listed depend on the IISAdmin
	Service, the the IISAdmin Service is started automatically when the W3SVC
	service is started.
	
	For additional information on finding the short names of services, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q271362 How to Find the Short Names of Services
	
	MORE INFORMATION
	================
	
	Do not use IISReset to force IIS configuration changes to be saved to the
	metabase. Only use IISReset to recover from serious problems that a Web server
	experiences. For example, when a Web server stops responding (hangs) or crashes,
	or when 100% CPU utilization occurs.
	
	For more information, see the notes in the IISReset window in the MMC.
	
	Additional query words: IIS IISRESET Metabase
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
