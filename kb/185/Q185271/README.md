---
layout: page
title: "Q185271: XADM: Orphaned LV Errors Running ESEUTIL Consistency Checker"
permalink: /kb/185/Q185271/
---

## Q185271: XADM: Orphaned LV Errors Running ESEUTIL Consistency Checker

{% raw %}

	Article: Q185271
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you are running ESEUTIL in integrity mode (ESEUTIL /G <dbname> /X),
	the output contains information similar to the following:
	
	  ERROR: orphaned LV (lid 62322, size 80682). Non-corrupting error
	  ERROR: node [514410:0]: leaf node check failed
	
	CAUSE
	=====
	
	Long values (LVs) are created by the Exchange database engine when a column is
	too large to store with the rest of the record. Large columns are broken into
	separate groupings, which are the long values. Long values are stored in a
	separate binary tree (B-Tree), and each LV is given a table-wide unique
	identifier (the LID, or long value ID).
	
	To save database space, the Exchange database engine allows multiple records to
	share the same long value (similar to, but not really related to the information
	store's concept of single-instance storage for messages). To do this, a
	reference count (refcount) is attached to each long value. When the refcount
	reaches zero, the long value is deleted.
	
	In a rare case where the Exchange database crashes after deferencing a long value
	but before expunging it from the database, the long value is "orphaned." Its
	refcount will be zero, but it will never be removed. Orphaned long values are
	invisible to anyone using the database because they are logically deleted, but
	they still take up space because they have not been physically removed.
	
	WORKAROUND
	==========
	
	This is a harmless error. The orphaned LVs take up space but do not interfere
	with the operation of the database. You can remove the orphaned LVs and reclaim
	the space using defragmentation.
	
	However, it is recommended that you perform defragmentation only if the space
	occupied by orphaned LVs is a significant percentage of the total database
	space. This value can be determined by looking at the size reported in the error
	message.
	
	To remove orphaned long values and reclaim the space, perform the following
	steps:
	
	1. Stop either the directory or the information store service, depending on
	  which database the errors were reported against.
	
	2. Run ESEUTIL /d /ds or ESEUTIL /d /ispriv or ESEUTIL /d /ispub to defragment
	  the database.
	
	3. After ESEUTIL completes with no errors, restart the Exchange services.
	
	4. Perform a full online backup of the information store databases.
	
	MORE INFORMATION
	================
	
	In Exchange 5.5, ESEUTIL run in integrity or repair mode (ESEUTIL /g or ESEUTIL
	/p) will only detect the orphaned LVs. To remove the orphaned long values, you
	must run ESEUTIL and defragment (ESEUTIL /d) the affected database.
	
	Additional query words: MDB long-value
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WINDOWS:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
