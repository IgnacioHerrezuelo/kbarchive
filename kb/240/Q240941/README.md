---
layout: page
title: "Q240941: An Introduction to the IIS Metabase"
permalink: /kb/240/Q240941/
---

## Q240941: An Introduction to the IIS Metabase

{% raw %}

	Article: Q240941
	Product(s): Internet Information Server
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbDSupport kbiis400
	Last Modified: 05-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The metabase is a structure for storing Internet Information Server (IIS)
	configuration settings. It performs some of the same functions as the Windows
	system registry but is specific to Internet Information Server version 4.0. New
	keys and values have been added for finer and more flexible control of IIS.
	
	When a system is upgraded from IIS 3.0 or earlier to IIS 4.0, the configuration
	parameters that were previously set in the registry are migrated to the
	metabase. When IIS starts, it loads the metabase into memory, where it is
	available until IIS shuts down. The metabase is stored in a special format file
	by default named Metabase.bin in the Inetsrv folder in which IIS is normally
	installed.
	
	Like the registry, the metabase is organized in a hierarchical structure that
	mirrors the structure of your IIS installation. It is made up of nodes, keys,
	and subkeys. The main organization is by node, with each node in the metabase
	structure representing a site or directory. Beneath the nodes are keys that may
	contain one or more IIS configuration values called metabase properties. The
	metabase keys correspond to individual configuration elements of IIS; each key
	contains properties that affect the configuration of its associated directory or
	site.
	
	The structure of the metabase facilitates different settings of a property for
	different nodes. For example, the MaxBandwidth property setting can be different
	for each virtual site. However, metabase properties are inherited. This means
	that those parameters that are configured at higher levels, such as the Web site
	level, will affect the lower levels. But if you set a specific property for an
	individual site, virtual site, or virtual directory, changes made at a higher
	level will not automatically override the lower-level individual setting. Note
	that when the metabase is searched for configuration information, it is
	enumerated from the bottom, or subkey, to top, or node.
	
	Many of the metabase parameters can be configured from the Internet Service
	Manager snap-in for the Microsoft Management Console (MMC). Additional tools are
	also available for further tuning of the metabase.
	
	Caution:
	
	Configuring properties in the metabase incorrectly can cause problems, including
	the failure of a Web site or FTP site. If you make mistakes, your Web site or
	FTP site's configuration could be damaged. You should edit metabase properties
	only for settings that you cannot adjust in the user interface. Be very careful
	whenever you edit the metabase directly.
	
	There are two main ways to edit the metabase:
	
	- IIS Administration Script Utility (Adsutil): Adsutil.vbs is a Visual Basic
	  Script utility that uses Active Directory Service Interfaces (ADSI) to
	  manipulate the configuration of IIS. Run this script using CScript, which is
	  installed with the Windows Scripting Host as part of the Windows NT Option
	  Pack. Cscript.exe is installed to %system root%/System32. Adsutil.vbs is
	  installed to %system root$/System32/Inetsrv/Adminsamples.
	
	- Mdutil.exe: This utility is available on the Option Pack CD-ROM. It can be
	  utilized from: \Ntoppak\En\X86\Winnt.srv\Mdutil.exe.
	
	MORE INFORMATION
	================
	
	For more information on the structure of the metabase, please consult the IIS
	4.0 product documentation.
	
	For additional information on manipulating the metabase, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q193152 Preserving Virtual Directories and Servers During Uninstall
	
	  Q229814 Configuring IIS to Handle Heavy Usage
	
	  Q234429 How to Manually Restore the Metabase When No Proper Backup Exists or
	  the MMC Won't Start
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbiis400 
	Technology        : kbiisSearch kbiis400
	Version           : winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
