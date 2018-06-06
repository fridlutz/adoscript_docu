---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_VERSION_USAGE"
tags: 1.3 1.5
---

GET_ATTRPROF_VERSION_USAGE returns a LEO string with all object which are referencing the attribute profile version specified by apversionid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_VERSION_USAGE apversionid:id .


#-->RESULT ecode:intValue usage:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`usage`|strValue|

# Remarks:

The return value usage is a LEO string with 0 to n lines of the following layout:  
REF srcmodelid:intValue srcobjid:intValue '\n'

# See Also:  



Example:

