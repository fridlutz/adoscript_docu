---
layout: commandcall
category: CommandCall
title: "RENAME_ATTRPROF_DIRECTORY"
tags: 1.3 1.5
---

RENAME_ATTRPROF_DIRECTORY renames the existing attribute profile directory specified in apdirid to the STRING value given in apdirname.

# Syntax:  

```adoscript
{% raw %}
CC "Core" RENAME_ATTRPROF_DIRECTORY apdirid:id apdirname:strValue


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirid`|id, the directory to be renamed is passed in apdirid.|
|`apdirname`|strValue, the new directory name is passed in apdirname.|

# Returns:  

|`ecode`|intValue, the result ecode is set to zero if function succeeded and to a non zero value if failed.|

# Remarks:



# See Also:  

[DELETE_ATTRPROF_DIRECTORY](delete_attrprof_directory.html "DELETE_ATTRPROF_DIRECTORY")  


Example:

