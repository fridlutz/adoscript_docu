---
layout: commandcall
category: CommandCall
title: "CREATE_ATTRPROF_DIRECTORY"
tags: 1.3 1.5
---

CREATE_ATTRPROF_DIRECTORY creates a new attribute profile directory with the name apdirname. Optional it is created as a subdirectory of superapdirid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_ATTRPROF_DIRECTORY apdirname:strValue [superapdirid:id] .


# --> RESULT ecode:intValue apdirid:id .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirname`|strValue, the directory name is specified in apdirname.|
|`superapdirid`|id, the super directory is specified in superapdirid.|

# Returns:  

|`ecode`|intValue, the result ecode is set to zero if function succeeded and to a non zero value if failed.|
|`apdirid`|id, the result apdirid contains the id of the new created attribute profile directory.|

# Remarks:




# See Also:  

[DELETE_ATTRPROF_DIRECTORY](delete_attrprof_directory.html "DELETE_ATTRPROF_DIRECTORY")  


Example:

