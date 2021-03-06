---
layout: page
title: "Q246309: How to Replace a Missing IIS In-Process Application in MTS"
permalink: /kb/246/Q246309/
---

## Q246309: How to Replace a Missing IIS In-Process Application in MTS

{% raw %}

	Article: Q246309
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In the Transaction Server Packages Installed, the IIS in-process applications
	package is missing.
	
	Also, when you try to set a site or virtual directory as an application, you may
	receive the following error message:
	
	  An error occurred getting or setting a configuration parameter 0x80010401
	
	CAUSE
	=====
	
	There are multiple causes for this error, including the following:
	
	- Errors returned from using IISSYNC to replicate a metabase.
	
	- Errors during install in regards to Transaction Server setup.
	
	- The package may be deleted from the registry.
	
	RESOLUTION
	==========
	
	At the REGEDIT4 line, copy the following into a *.reg file and run it against
	your registry:
	
	  
	
	  REGEDIT4
	
	  [HKEY_CLASSES_ROOT\AppID\{3D14228C-FBE1-11d0-995D-00C04FD919C1}]
	  "RunAs"="Interactive User"
	
	  [HKEY_CLASSES_ROOT\CLSID\{3D14228C-FBE1-11d0-995D-00C04FD919C1}]
	  "AppID"="{3D14228C-FBE1-11d0-995D-00C04FD919C1}"
	
	  [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Transaction Server\Packages\{3D14228C-FBE1-11d0-995D-00C04FD919C1}]
	  "Activation"="Inproc"
	  "Changeable"=""
	  "Name"="IIS In-Process Applications"
	  "Description"=" "
	  "System"="N"
	  "Latency"=dword:000000b4
	  "NeverShutdown"="Y"
	  "Deleteable"="N"
	  "CreatedBy"="Microsoft Internet Information Server(tm)"
	  "SecurityEnabled"="N"
	  "Authentication"=dword:00000004
	  "Authorization"=hex:01,00,04,80,34,00,00,00,50,00,00,00,00,00,00,00,14,00,00,\ 
	 00,02,00,20,00,01,00,00,00,00,00,14,00,01,00,00,00,01,01,00,00,00,00,00,05,\ 
	 12,00,00,00,00,00,00,00,01,05,00,00,00,00,00,05,15,00,00,00,85,78,18,0e,b8,\ 
	 1a,c4,34,24,0d,b1,12,f4,01,00,00,01,05,00,00,00,00,00,05,15,00,00,00,85,78,\ 
	 18,0e,b8,1a,c4,34,24,0d,b1,12,f4,01,00,00
	  "UserId"="Interactive User"
	
	  [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Transaction Server\Packages\{3D14228C-FBE1-11d0-995D-00C04FD919C1}\Components]
	
	  [HKEY_LOCAL_MACHINE\SOFTWARE\Classes\AppID\{3D14228C-FBE1-11d0-995D-00C04FD919C1}]
	  "RunAs"="Interactive User"
	
	  [HKEY_LOCAL_MACHINE\SOFTWARE\Classes\CLSID\{3D14228C-FBE1-11d0-995D-00C04FD919C1}]
	  "AppID"="{3D14228C-FBE1-11d0-995D-00C04FD919C1}"
	
	  *[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Transaction Server\Components\{99169CB0-A707-11d0-989D-00C04FD919C1}]
	  "ProgID"="IISWAM.W3SVC"
	  "Inproc"="Y"
	  "Local"="N"
	  "Remote"="N"
	  "Enabled"="N"
	  "ThreadingModel"="Free"
	  "DllServer"="<I>DriveLetter</I>:\\%Windir%\\System32\\inetsrv\\wam.dll"
	  "Package"="{3D14228C-FBE1-11d0-995D-00C04FD919C1}"
	  "SupportsInternet"="N"
	  "Description"=" "
	  "Transaction"="Not Supported"
	  "System"="N"
	  "Wrapped"="N"
	
	  [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Transaction Server\Packages\{3D14228C-FBE1-11d0-995D-00C04FD919C1}\Components\{99169CB0-A707-11d0-989D-00C04FD919C1}]
	  "SecurityEnabled"="Y"
	  "Authentication"=dword:00000004
	
	When these registry changes are imported into your registry, they replace the IIS
	in-process application only. After you import this registry information, the
	only package that will exist in the Transaction Server IIS in-process
	application is IISWAM.W3SVC. You can only re-create these through the registry,
	and generally, that is between various installations of the Windows NT Option
	Pack, because it is only these components that have static CLSIDs.
	
	After you import this registry information, none of your sites and virtual
	directories that are set to run in process will be registered properly in
	Transaction Server. You will need to remove and re-create all of your sites and
	virtual directories that are running in process as Applications.
	
	To verify that these sites are registered in Transaction Server as applications,
	and are running under the context of the IIS in-process application, check the
	sites or virtual directory properties. If they have a Remove button, but do not
	have the Separate Memory Address Space check box selected, then they are an
	application that is a component of the IIS in-process application.
	
	For each site that has a Remove button, but is not enabled to run in a separate
	memory space, re-create that site as an application. To do this, do the
	following:
	
	1. For each site or virtual directory, open the Properties, and then click the
	  Home Directory tab.
	
	2. In the Application section, click Remove, and then click Apply (to completely
	  remove it)
	
	3. Click Create, and then click OK.
	
	Important: After you import this information into your registry, do not restart
	or stop the IIS associated services (Web Publishing, IIS Administrative, and so
	on). The components are still registered in the metabase until the services (or
	the server) is restarted. If you restart, you run the risk of removing
	information related to any custom components. This is due to the way that
	information is stored in the metabase and synced to the Metabase.bin file that
	holds the information.
	
	For additional information on the metabase, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q240941 An Introduction to the IIS Metabase
	
	Additionally, you must use Dcomcnfg.exe to reset permissions on the default
	packages and the existing packages.
	For additional information regarding Dcomcnfg, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q176799 INFO: Using DCOM Config (DCOMCNFG.EXE) on Windows NT
	
	WORKAROUND
	==========
	
	If this resolution does not work to replace the missing IIS in-process
	application and repair Transaction Server, then you can restore from a known
	backup, or remove and reinstall the Windows NT Option Pack to rebuild IIS,
	Transaction Server, and the metabase.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
