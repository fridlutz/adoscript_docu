---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_DIRECTORY_NAME"
tags: 1.3 1.5
---

GET_ATTRPROF_DIRECTORY_NAME returns the name of the attribute profile directory specified in apdirid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:id .


#-->RESULT ecode:intValue apdirname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirid`|id, the directory is specified by its id passed in apdirid.|

# Returns:  

|`ecode`|intValue, the result ecode is set to zero if function succeeded and to a non zero value if failed.|
|`apdirname`|strValue, the result apdirname of type STRING returns the name of the specified attribute profile directory.|

# Remarks:



# See Also:  

[DELETE_ATTRPROF_DIRECTORY](delete_attrprof_directory.html "DELETE_ATTRPROF_DIRECTORY")  


Example:

