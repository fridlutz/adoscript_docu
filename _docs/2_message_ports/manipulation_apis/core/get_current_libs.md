---
layout: commandcall
category: CommandCall
title: "GET_CURRENT_LIBS"
tags: 1.3 1.5
---

GET_CURRENT_LIBS retrieves names and ids of the currently loaded library.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_CURRENT_LIBS

#--> RESULT ecode:intValue 
			applib:strValue applibid:intValue 
			bplib:strValue bplibid:intValue 
			welib:strValue welibid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`applib`|strValue, name of ADOxx Application library|
|`applibid`|intValue, id of the ADOxx Application library (= Default_ApplicationLibrary)|
|`bplib`|strValue, name of the ADOxx Dynamic library|
|`bplibid`|intValue, id of the ADOxx Dynamic library|
|`welib`|strValue, name of the ADOxx Static library|
|`welibid`|intValue, id of the ADOxx Static library|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_CURRENT_LIBS
CC "AdoScript" INFOBOX ("You are currently working with the library \n" + 
                         applib + " (" + STR applibid + ")\n" +
                         bplib + " (" + STR bplibid + ")\n" +
                         welib + " (" + STR welibid + ")")

{% endraw %}
```
{: .line-numbers}
Retrieves the names of the libraries and displays them in an infobox.

