---
layout: commandcall
category: CommandCall
title: "GET_APPMODEL_ID"
tags: 1.3 1.5
---

GET_APPMODEL_ID returns the ID of the ApplicationModel with the given name.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_APPMODEL_ID appmodelname:strValue

#--> RESULT ecode:intValue appmodelid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`appmodelname`|strValue, the name of the application model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`appmodelid`|intValue, the ID of the application model or -1 if an error has occured.|

# Remarks:



# See Also:  

[GET_APPMODEL_INFO](get_appmodel_info.html "GET_APPMODEL_INFO")  


Example 1:

```adoscript
{% raw %}

# Assume there is an ApplicationModel "Test"
CC "Core" GET_APPMODEL_ID appmodelname:"Test"

# show the ID
CC "AdoScript" INFOBOX ("The ID is: " + STR (appmodelid))

{% endraw %}
```
{: .line-numbers}

