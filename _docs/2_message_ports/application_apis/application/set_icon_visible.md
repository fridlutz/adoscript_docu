---
layout: commandcall
category: CommandCall
title: "SET_ICON_VISIBLE"
tags: 1.3 1.5
---

SET_ICON_VISIBLE shows or hides a smart icon in a component's quick access bar.

# Syntax:  

```adoscript
{% raw %}
CC "Application" SET_ICON_VISIBLE [ component:Component ] name:strValue visible: 0|1

Component :	"acquisition" | "modeling" | "analysis" |
			"simulation" | "evaluation" | "importexport" | 
			"all" .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}
# Parameters:  

|`component`|strValue, name of the component as displayed in the list above|
|`name`|strValue, name of the icon|
|`visible`|0|1|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Names of built-in smart icons and default visibility  
* BACK - Navigate back	1
* FWD	- Navigate forward	1
* LIST - Window list	1
* EXCEL - Acquisition tables	1
* NEW - New model	1
* MLOAD - Open model	1
* SAVE - Save model	1
* MPRINT - Print model	1
* APLOAD - Application models	0
* UNDO - Undo	1
* REDO - Redo	1
* CUT - Cut	1
* COPY - Copy	1
* PASTE - Paste	1
* TRANSFER - Transer attributes	1
* VGRAPH - View graphics	1
* VTABLE - View table	1
* ZOOM - Zoom	1
* ONEONE - Scale 1:1	1
* ALL - Make all visible	1
* RAACT - Snap grid active	1
* RAVIS - Snap grid visible	1
* HOVER - Modeling assistent	1
* RIGHTANG - Right angled connectors	1
* POSSZ - Position and Size	1
* CHNG - Global change	1
* LAYALG - Layout	1
* HORI - Align horizontally	1
* VERT - Align vertically	1
* AREA - Drawing area size	1
* MGGEN - Graphics generation	1
* COST - Time and costs	1
* QUERI - Queries/Reports	1
* USQUERI - Predefined queries	1
* RELTABS - Relation tables	1
* ANALY - Calculation	1
* PATH - Path analysis	1
* WORKL - Capacity analysis	1
* VOL - Workload analysis (steady-state)	1
* VOLDYN - Workload analysis (fixed time period)	1
* AGENT - Agents	1
* OFFLINE - Offline animation	1
* DELSIM - Delete simulation results	1
* DELCACHE - Free simulation cache	1
* SLOAD - Open model (simulation comp)	1
* SPRINT - Print model (simulation comp)	1
* SGGEN - Graphics generation (simulation comp)	1
* FLOW - FlowMark audit trail evaluation	1
* RESCMP - Comparison of results	1
* USEVAL - Predefined queries	1
* CCC_IST - Actual-process cost analysus	1
* CCC_PLAN - Plan-process cost analysis	1
* ADLIM - ADL import	1
* ADLEX - ADL export	1
* HTML - HTML export	1
* DOCU - RTF export	1
* EXCUST - Documentation options	1

The smart icons "BACK", "FWD" and "LIST" (window navigation and window list) are component independent. Showing/hiding of these smart icons cannot be applied on just one component' quick access bar.

Note that the visibility of some icons also depend on the configuration of your application library. I.e. the default visibility as in the list above assumes a corresponding library configuration. The icons which visibility depend on the application library definition are USQUERI, USEVAL, LAYALG .

# See Also:  



Example 1:

```adoscript
{% raw %}

The following statements make the "Application models" smart icon visible and the "HTML export" smart icon invisible:
CC "Application" SET_ICON_VISIBLE name:"APLOAD" visible:1
CC "Application" SET_ICON_VISIBLE name:"HTML" visible:0

{% endraw %}
```
{: .line-numbers}

