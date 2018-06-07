---
layout: commandcall
category: CommandCall
title: "GET_ROOT_ATTRPROFDIR_ID"
tags: 1.3 1.5
---

The command GET_ROOT_ATTRPROFDIR_ID returns the apdirid of the invisible toplevel AttrProf directory ID.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ROOT_ATTRPROFDIR_ID


#-->RESULT ecode:intValue apdirid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, if the function succeeded ecode returns "0". Else a non zero value error code is returned.|
|`apdirid`|id|

# Remarks:




# See Also:  



Example 1:

```adoscript
{% raw %}

# get root AttrProf directory ID
CC "Core" GET_ROOT_ATTRPROFDIR_ID

# get all visible top level directories
CC "Core" GET_ALL_ATTRPROF_SUBDIRS apdirid:(apdirid)

CC "AdoScript" INFOBOX (apdirids)

{% endraw %}
```
{: .line-numbers}
Interesting:  
- get root AttrProf directory ID  
- get all sub directories  
- print list of IDs  
