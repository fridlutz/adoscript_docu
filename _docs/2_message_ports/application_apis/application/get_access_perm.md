---
layout: commandcall
category: CommandCall
title: "GET_ACCESS_PERM"
tags: 1.3 1.5
---

GET_ACCESS_PERM checks for the current user, whether a component is enabled or not.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_ACCESS_PERM Component

Component :	"aqc" | "modelaccess" | "modeldescr" | "modelstate" | "stdqueries" | 
			"defqueries" | "reltables" | "anaeval" | "pathsim" | "volsim" | 
			"steadywlsim" | "fixedwlsim" | "agents" | "flowmark" | "rescomp" | 
			"evalqueries" | "dyneval" | "adl" | "xml" | "fdl" | "case40" | 
			"objectif" | "ccc" | "docutk" | "attrprof" | "classhier" | "nonewdb"

#--> RESULT ecode:intValue access: 0|1 .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, contains the name of the component which should be checked.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`access`|0|1, 1 if the acces is enabled and 0 otherwise.|

# Remarks:

The names in the list above correspond to the components in the configuration notebook.

![](/images/GET_ACCESS_PERM.png)

# See Also:  



Example 1:  
Checks if the user has sufficient access to generate documentation. If not, displays an error message.  
```adoscript
{% raw %}

CC "Application" GET_ACCESS_PERM "docutk"
IF (access = 0) {
    CC "AdoScript" ERRORBOX "The user has no access rights for the documentation component"
}

{% endraw %}
```
{: .line-numbers}

