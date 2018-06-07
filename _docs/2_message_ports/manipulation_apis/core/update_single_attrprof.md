---
layout: commandcall
category: CommandCall
title: "UPDATE_SINGLE_ATTRPROF"
tags: 1.3 1.5
---

The command UPDATE_SINGLE_ATTRPROF forces a single attribute profile to be updated.

# Syntax:  

```adoscript
{% raw %}
CC "Core" UPDATE_SINGLE_ATTRPROF apversionid:id.


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|id, the parameter apversionid contains the ID of the attribute profile version to be updated.|

# Returns:  

|`ecode`|intValue, the return value ecode is set to "0" is command was executed successfully and to non zero value if it failed.|

# Remarks:

Update means it is completely reloaded from the database.  
That command updates the attribute profile only in the core and may not affect any user interface! Use that command before editing an attribute profile to ensure that the data is valid!




# See Also:  



Example 1:

```adoscript
{% raw %}

# determine AP version ID - up to you :)

# update
CC "Core" UPDATE_SINGLE_ATTRPROF apversionid:(apvid)

IF ((ecode)!=0)
{
  CC "AdoScript" ERRORBOX ("Error "+(STR ecode)+" occured!")
  EXIT
}

CC "AdoScript" INFOBOX ("Updated all attribute profiles successfully!")

{% endraw %}
```
{: .line-numbers}

