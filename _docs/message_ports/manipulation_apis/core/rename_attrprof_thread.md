---
layout: commandcall
category: CommandCall
title: "RENAME_ATTRPROF_THREAD"
tags: 1.3 1.5
---

RENAME_ATTRPROF_THREAD renames an existing AttrProf thread and also all of its versions.

# Syntax:  

```adoscript
{% raw %}
CC "Core" RENAME_ATTRPROF_THREAD apthreadid:id apthreadname:strValue .


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apthreadid`|id, the AttrProf thread is specified by its id passed in apthreadid.|
|`apthreadname`|strValue|

# Returns:  

|`ecode`|intValue, the result ecode is set to a non-zero value if renaming fails.|

# Remarks:




# See Also:  

[CREATE_ATTRPROF_VERSION](create_attrprof_version.html "CREATE_ATTRPROF_VERSION")  


Example:

