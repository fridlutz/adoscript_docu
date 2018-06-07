---
layout: commandcall
category: CommandCall
title: "EXEC_NOTEBOOK"
tags: 1.3 1.5
---

EXEC_NOTEBOOK shows a notebook of a certain object.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" EXEC_NOTEBOOK objid:id .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

Attention:  
This command does not work for model notebooks!

# See Also:  



Example:




