---
layout: page
title: "Q139380: Multihomed WINS Server Replication Partner Failures"
permalink: /kb/139/Q139380/
---

## Q139380: Multihomed WINS Server Replication Partner Failures

{% raw %}

	Article: Q139380
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After setting up replication between multi-homed WINS servers, some data may not
	replicate properly and the following error may be logged in the event log:
	
	  Event 4102: "Connection was aborted by remote client".
	
	CAUSE
	=====
	
	When configuring replication partners, only one IP address may be entered for a
	given partner. If you attempt to add another IP address for the same replication
	partner, WINSADMN realizes that this is the same system as the one previously
	already entered, and switches the IP address in the list to the one that the
	WINS server is bound to on the remote machine.
	
	However, when replication actually occurs, Windows Sockets is the interface used.
	The outgoing pull request uses socket()/bind()/connect() calls, and on the bind
	it specifies INADDR_ANY. This means that the outgoing call can be sourced from
	any IP address on a computer. If it's sourced from any IP address other than the
	one that the WINS server is bound to, replication fails. The event log will
	contain "Connection aborted by remote client." The replication fails because the
	WINS server being contacted compares the source address of the incoming request
	to its list of authorized replication partners.
	
	RESOLUTION
	==========
	
	WINSADMN.EXE (the WINS manager) has been modified to allow each IP address on a
	multi-homed machine to be entered as a replication partner on the other machines
	it replicates with. Each IP address should be entered as a replication partner
	on all machines that will replicate with a multi- homed computer.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. This
	problem was corrected in the latest Windows NT 3.51 U.S. Service Pack. For
	information on obtaining the Service Pack, query on the following word in the
	Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt multihomed
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : winnt:3.5,3.51
	
	=============================================================================
	

{% endraw %}
