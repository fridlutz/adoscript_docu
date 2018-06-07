---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODIFIED"
tags: 1.3 1.5
---

GET_ALL_MODIFIED returns a string containing the IDs of all modified models.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_ALL_MODIFIED .


# --> RESULT modelids:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`modelids`|strValue|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

The following code does the same as CC "Modeling" SAVE_ALL:
CC "Modeling" GET_ALL_MODIFIED
FOR modelid in:(modelids) {
   CC "Modeling" SAVE modelid:(VAL modelid)
}

{% endraw %}
```
{: .line-numbers}


