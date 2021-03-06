---
layout: page
title: "Q119884: PC Ext: Increasing Retry Count for LAN-Based Mail"
permalink: /kb/119/Q119884/
---

## Q119884: PC Ext: Increasing Retry Count for LAN-Based Mail

{% raw %}

	Article: Q119884
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0,3.2,3.2a,3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 3.0, 3.2, 3.2a, 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	It is possible to set retries for each external postoffice defined on a network.
	This might be desirable when frequent "retry count exceeded" messages are
	displayed in the SYSTEM.LOG file. The ADMIN.EXE program directly supports
	setting the retries for postoffices with routing defined as Direct via Modem.
	Once this count has been set, it is retained when the postoffice routing is
	modified to Direct via MS-DOS drive.
	
	To set the retry count for mail destined to a specific postoffice:
	
	1. Run ADMIN.EXE at the postoffice that is the source of the mail.
	
	2. Select External-Admin, Modify and choose the destination network name and
	  postoffice.
	
	3. Specify routing to be Direct via Modem.
	
	4. Answer yes to the Modify? prompt.
	
	5. Select External-Admin, Setup and press <ENTER> at the network name.
	
	6. Select the Options and Retries menu item.
	
	7. Enter the desired number of Retries for the postoffice. Escape back and
	  select Yes to update the record.
	
	8. Select External-Admin, Modify and change the routing of this postoffice back
	  to its former routing, such as Direct via MS-DOS Drive.
	
	9. Answer yes to modify the postoffice.
	
	  This will have reset the count in the XTN file.
	
	NOTE: This change does not immediately become effective. The External program,
	which makes use of this count, caches this information in memory and will not
	have the new value until it updates from the postoffice.
	
	Updating occurs when External starts and when the update interval is reached. The
	update interval is normally five minutes, but it can be set to a different value
	through command line and INI settings using the IntervalUpdate= parameter. See
	Chapter 12 of the "Administrator's Guide" for more information on External
	parameters.
	
	MORE INFORMATION
	================
	
	How the Retry Count is Used
	---------------------------
	
	External will cycle through the queues of external postoffices looking for mail
	to be dispatched. If mail is to be transferred and an attempt to deliver this
	mail is unsuccessful, External will update the queue to reflect that an
	additional retry occurred. Each time an error occurs on a specific mail item,
	its retry count is incremented. After incrementing, the number is compared to
	the maximum retry count associated with the destination postoffice. If the
	number is equal to or exceeds the retry count, the mail is considered
	undeliverable and will be returned to the originator.
	
	The default retry count for a mail item is 3. This means that after 3 attempts,
	the item is returned and the following message is placed into the SYSTEM.LOG:
	
	  [005] Mail Retry count exceeded sending to: ...
	
	How Changing the Retry Count Effects Mail Delivery
	--------------------------------------------------
	
	When there is only one MTA (External) processing mail at a postoffice, the span
	of time before a mail item is returned would generally be about 15 minutes. This
	is based on a retry count of 3 and an interval of 5 minutes between MTA cycles.
	If External cannot make a full cycle of all postoffices in 5 minutes, the total
	time could be longer. This 15 minutes might be long enough for temporary network
	problems to be eliminated and for the item to successfully transfer.
	
	When multiple MTAs operate in a mail configuration, the span of time before the
	retry count is exceeded is difficult to predict. Consider a situation in which
	three MTAs operate. It is possible that one MTA would have just finished
	updating the retry count for a mail item and another MTA would make another
	attempt. If all three MTAs were close behind one another, then the default retry
	count could be exceeded in a matter of a few minutes. In this case, updating the
	retry count could provide a needed time buffer.
	
	The best scenario is one in which the network, routers, and servers rarely fail.
	If at all possible, steps should be taken to remedy problems in these areas
	rather than have excessive retries.
	
	The Retry Count Effects Notification of Mail Problems
	-----------------------------------------------------
	
	If External is persistent (high retry count) in its attempt to deliver mail, mail
	can sit in queues for a long time before the sender is notified that there is a
	delivery problem. As explained above, this is dependent on the number of MTAs
	operating and the cycle interval.
	
	NOTE: Until the retry count is exceeded, the sender has no indication that there
	are delivery problems. For the known unreliable network connections, the
	administrator is faced with the task of balancing the competing priorities of
	persistent mail delivery vs. the senders need to know that his mail has not yet
	been delivered.
	
	Additional query words: 3.00 3.20 3.20a 3.50
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN320a kbMailPCN300 kbMailPCN350
	Version           : WINDOWS:3.0,3.2,3.2a,3.5
	
	=============================================================================
	

{% endraw %}
