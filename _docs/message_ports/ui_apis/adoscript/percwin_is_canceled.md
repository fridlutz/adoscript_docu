---
layout: commandcall
category: CommandCall
title: "PERCWIN_IS_CANCELED"
tags: 1.3 1.5
---

PERCWIN_IS_CANCELED checks the "canceled" status of the percentage window.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" PERCWIN_IS_CANCELED

# --> RESULT ecode:intValue canceled:boolValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue|
|`canceled`|boolValue, is set 1 if the user has pushed the percentage window's cancel button since it has been created with PERCWIN_CREATE.|

# Remarks:

When PERCWIN_IS_CANCELED returns a nonzero ecode this means that currently no percentage window is existing.

# See Also:  

[PERCWIN_CREATE](percwin_create.html "PERCWIN_CREATE")  
[PERCWIN_DESTROY](percwin_destroy.html "PERCWIN_DESTROY")  
[PERCWIN_SET](percwin_set.html "PERCWIN_SET")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" PERCWIN_CREATE with-cancel-button
        title:"Push the cancel button"
SET count:10000
FOR i from:1 to:(count) {
    CC "AdoScript" PERCWIN_IS_CANCELED
    IF (canceled) {
        BREAK
    }
    CC "AdoScript" PERCWIN_SET percentage:(100.0 ** i / count)
            text:(STR i + "/" + STR count)
    CC "AdoScript" SLEEP ms:5
}
CC "AdoScript" PERCWIN_DESTROY

{% endraw %}
```
{: .line-numbers}

