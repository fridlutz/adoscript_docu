---
layout: commandcall
category: CommandCall
title: "CLOSE_NOTEBOOK"
tags: 1.3 1.5
---

CLOSE_NOTEBOOK closes the notebook of a certain object.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CLOSE_NOTEBOOK objid:intValue.


# --> RESULT ecode:intValue.

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

Attention:  
Closing the own notebook while executing a PROGRAMCALL is not allowed and leads to a crash.

# See Also:  



Example:




