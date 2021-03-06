---
layout: page
title: "Q298985: AUTOMAP: &quot;Unable to Get Directions&quot; Err Msg Creating Route"
permalink: /kb/298/Q298985/
---

## Q298985: AUTOMAP: &quot;Unable to Get Directions&quot; Err Msg Creating Route

{% raw %}

	Article: Q298985
	Product(s): Microsoft Automap
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Streets and Trips 2001 
	- Microsoft MapPoint 2002 
	- Microsoft MapPoint 2001 
	- Microsoft Streets & Trips 2002, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to create a route by using one of the programs listed at the
	beginning of this article, you may receive an error message similar to the
	following
	
	  Unable to get directions from <location> to <location>. One of
	  the areas may not contain necessary connectors such as ferry routes or main
	  roads. Move one or both of the stops, and try again.
	
	where the locations listed are part of the route that you are attempting to
	create.
	
	You may also receive this error message when you use the Avoid Area command to
	create an alternate route.
	
	CAUSE
	=====
	
	This behavior can occur if you attempt to create a route through an area for
	which the program does not contain street or highway information.
	
	For example, if you attempt to create a route through a national park, a military
	base, or any area where travel is restricted, the street and highway information
	may not be available to plot through those areas. As a result, the program plots
	an alternate route around the area in question.
	
	This behavior is by design. When no data point information is available for the
	routing program for a selected route, the program plots the trip by an alternate
	route, where possible. If the program is unable to plot an alternate route, you
	receive the error message described in the "Symptoms" section of this article.
	
	RESOLUTION
	==========
	
	To work around this issue, plot two separate routes, as follows:
	
	1. Plot the first route from your start point to the place at which the data
	  becomes unavailable.
	
	2. Plot a second route starting from the place at which the data is available
	  again, and onward to your final destination.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbExpediaSearch kbMapptSearch kbMapPoint2001 kbExpediaStreets2001 kbExpediaStreets2002 kbMapPoint2002
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
