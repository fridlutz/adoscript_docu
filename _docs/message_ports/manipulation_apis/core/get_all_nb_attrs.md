---
layout: commandcall
category: CommandCall
title: "GET_ALL_NB_ATTRS"
tags: 1.3 1.5
---

GET_ALL_NB_ATTRS returns a list of all attribute IDs contained in the notebook of a certain class or relation class.


# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_NB_ATTRS classid:intValue .


#-->RESULT ecode:intValue attrids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|intValue, the ID of the class or relation class is passed via the parameter classid.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`attrids`|strValue|

# Remarks:


If no notebook is defined for that class, an empty container is returned.

# See Also:  



Example 1:

```adoscript
{% raw %}

# get class ID from class name
CC "Core" GET_CLASS_ID classname:"Dokument"
# get all Notebook attributes
CC "Core" GET_ALL_NB_ATTRS classid:(classid)
# and show them
CC "AdoScript" INFOBOX (attrids)

{% endraw %}
```
{: .line-numbers}

