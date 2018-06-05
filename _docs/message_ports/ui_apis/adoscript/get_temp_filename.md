---
layout: commandcall
category: CommandCall
title: "GET_TEMP_FILENAME"
tags: 1.3 1.5
---

GET_TEMP_FILENAME queries the operating system for a temporary filename.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" GET_TEMP_FILENAME .

#--> RESULT filename:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`filename`|strValue, contains the absolute path to a (not yet existing) file in the TEMP-directory.|

# Remarks:

The environment variable TEMP has to be set properly (this is usually the case on properly installed systems).

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" GET_TEMP_FILENAME
CC "AdoScript" INFOBOX ("The temporary file name is: " + filename)

{% endraw %}
```
{: .line-numbers}
Queries a temporary file name and displays it in an infobox  
