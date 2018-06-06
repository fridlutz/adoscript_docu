---
layout: commandcall
category: CommandCall
title: "UPDATE_ALL_ATTRPROFS"
tags: 1.3 1.5
---

The command UPDATE_ALL_ATTRPROFS forces alle attribute profiles to be updated.

# Syntax:  

```adoscript
{% raw %}
CC "Core" UPDATE_ALL_ATTRPROFS


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, the return value ecode is set to "0" is command was executed successfully and to non zero value if it failed.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# update
CC "Core" UPDATE_ALL_ATTRPROFS

IF ((ecode)!=0)
{
  CC "AdoScript" ERRORBOX ("Error "+(STR ecode)+" occured!")
  EXIT
}

CC "AdoScript" INFOBOX ("Updated all attribute profiles successfully!")

{% endraw %}
```
{: .line-numbers}

