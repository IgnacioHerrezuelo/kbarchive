---
layout: page
title: "Q216922: Certificate Server Does Not Create Backups of Installed Keys"
permalink: /kb/216/Q216922/
---

## Q216922: Certificate Server Does Not Create Backups of Installed Keys

{% raw %}

	Article: Q216922
	Product(s): Internet Information Server
	Version(s): winnt:1.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Certificate Server version 1.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Certificate Server does not create backups of installed keys. If you intend to
	use the certificate to encrypt persistent data such as e-mail, then you should
	ensure that some form of back up protects the private key for that certificate.
	If the key is unprotected, and is subsequently unavailable, then you will be
	unable to decrypt data encrypted with the certificate.
	
	MORE INFORMATION
	================
	
	The functions of a Certificate Server can be summarized as follows:
	
	   - Receive certificate requests.
	
	- Create certificates from the requests it receives.
	
	- Distribute or publish certificates.
	
	- Publish Certificate Revocation Lists (CRLs).
	
	Some applications, which encrypt persistent data such as e-mail, have an
	additional requirement to archive private keys of encryption certificates. This
	is to ensure a users access to the data in the event that they become
	unavailable. If that event occurs, the user can request a copy of the private
	key from the archive. Exchange Advanced Security has an additional service, the
	Key Manager Server (KMS), which performs this role.
	
	Microsoft CSPs store the private keys in the registry. If Roaming profiles are
	used, then the Windows NT infrastructure provides resilience for the private
	keys. If Roaming profiles are not available, or a third-party CSP is used that
	does not use the registry to store keys, separate provisions should be made to
	back up the keys.
	
	Additional query words: Certificate, Back-up, S/MIME
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbCertServSearch kbZNotKeyword3 kbCertServ100
	Version           : winnt:1.0,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
