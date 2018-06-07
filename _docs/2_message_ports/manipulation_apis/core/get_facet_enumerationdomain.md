---
layout: commandcall
category: CommandCall
title: "GET_FACET_ENUMERATIONDOMAIN"
tags: 1.3 1.5
---

GET_FACET_ENUMERATIONDOMAIN retrieves the enumeration domain facet from the specified attribute

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_FACET_ENUMERATIONDOMAIN attrid:id .


#-->RESULT ecode:intValue val:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attrid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`val`|strValue|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_CLASS_ID classname:"Ende"
CC "Core" GET_ATTR_ID attrname:"Typ" classid:(classid)
CC "Core" GET_FACET_ENUMERATIONDOMAIN attrid:(attrid)
CC "AdoScript" INFOBOX (val)

{% endraw %}
```
{: .line-numbers}

