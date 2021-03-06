---
layout: page
title: "Q242987: Host Security Domain Disappears from SNA Server Manager"
permalink: /kb/242/Q242987/
---

## Q242987: Host Security Domain Disappears from SNA Server Manager

{% raw %}

	Article: Q242987
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Operating System(s): 
	Keyword(s): kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp
	Last Modified: 08-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Host Security Domains (HSDs) may intermittently disappear from the SNA Server
	Manager. When this occurs, the following host security features no longer
	function:
	
	- Single Sign-On (SSO)
	- Password replications to or from a host (for example, a mainframe or AS/400)
	  system
	
	CAUSE
	=====
	
	When the SNA Host Account Cache (HAC) service (Snaudb.exe) operates in a backup
	role, it receives a new copy of the master database when it detects that its
	local copy is out of sync with the master copy. The backup SNA HAC service
	incorrectly stops itself after it successfully copies and reads the master Host
	Account Database. The local copy of the Host Account Database is deleted when
	the backup SNA HAC service stops. If the system running the backup SNA HAC
	service is promoted to be the primary domain controller (PDC) for the Windows NT
	domain while the HAC service is stopped, the HAC service becomes the Primary (or
	Master) HAC the next time it is started. It then creates a new Host Account
	Database because it does not have a local copy. When this occurs, the Host
	Security Domains that existed in the previous Host Account Database no longer
	exist. The SNA Server Manager sends RPC messages to the Host Account Database to
	get a list of the defined Host Security Domains when the SNA Server Manager is
	open. Because the HAC does not have any HSDs defined, it does not return any.
	Therefore, the SNA Server Manager does not display any HSDs. Because a new Host
	Account Database is created, the SSO and password replication features no longer
	function until the database is repopulated.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server 4.0. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server versions
	3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3.
	
	This problem was first corrected in SNA Server 4.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	After you apply the update, the backup SNA Server HAC services will no longer
	stop after they successfully copy and read the master Host Account Database.
	
	The following is a sequence that can lead to the problem described in this
	article:
	
	1. Backup Host Account database determines it is out of sync with the master
	  database.
	2. The master database is successfully copied to the local system and is
	  successfully read.
	3. The SNA HAC service stops, which causes the local Host Account Database to be
	  deleted.
	4. The system running the backup SNA HAC service is promoted from a Backup
	  Domain Controller (BDC) to a PDC because the original PDC is no longer
	  available for some reason.
	5. The SNA HAC service is started. It starts as the Primary (or Master) HAC, as
	  it determines its role from role of the Windows NT Server is it running on.
	6. A new Host Account Database is created because the local copy no longer
	  exists.
	7. SNA Server Manager is opened and the Host Security Domains that used to be
	  listed are no longer shown. In addition, the host security features no longer
	  function correctly.
	
	Every 15 minutes, backup Host Account Databases check with the master database to
	see if they're are still in sync. The databases use generation (for example,
	sequence) numbers to keep track of the changes that are made to the database.
	The generation numbers are incremented by 1 for each change that is made. If the
	backup database's generation number differs from the master database's
	generation number by 5 or more, the backup copies the master database locally.
	
	
	Starting with SNA Server 4.0 SP3, a backup HAC service will no longer delete its
	local Host Account database when the service is stopped if the master account
	database on the PDC is unavailable. For additional information about the update
	that prevents the backup host account database from being deleted when the
	master host account database is unavailable, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q240108 Backup Host Security Cache Deleted on Exit
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbSNA400sp4fix kbSNA400PreSP4fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
