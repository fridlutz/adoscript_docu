---
layout: commandcall
category: CommandCall
title: "DELETE_ATTRPROF_THREAD"
tags: 1.3 1.5
---

DELETE_ATTRPROF_THREAD deletes an existing attribute profil thread and all of its versions.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_ATTRPROF_THREAD apthreadid:intValue 

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apthreadid`|intValue, the id of the AttrProf|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The whole substructure of this thread will be deleted. All attribute profiles versions of this thread will be deleted as well.

# See Also:  

[CREATE_ATTRPROF_VERSION](create_attrprof_version.html "CREATE_ATTRPROF_VERSION")  


Example:

