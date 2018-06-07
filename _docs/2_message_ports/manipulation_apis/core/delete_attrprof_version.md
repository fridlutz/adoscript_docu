---
layout: commandcall
category: CommandCall
title: "DELETE_ATTRPROF_VERSION"
tags: 1.3 1.5
---

DELETE_ATTRPROF_VERSION deletes an existing attribute profil version of an attribute profile thread.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_ATTRPROF_VERSION apversionid:intValue


# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|intValue, the AttrProf version ID|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

# See Also:  

[CREATE_ATTRPROF_VERSION](create_attrprof_version.html "CREATE_ATTRPROF_VERSION")  


Example:

