---
layout: commandcall
category: CommandCall
title: "UNLOCK_SHELL"
tags: 1.3 1.5
---

Unlocks the access to all menus and smart icons after executing the given evaluation.

# Syntax:

```adoscript
{% raw %}
CC "Evaluation" UNLOCK_SHELL

# --> RESULT ecode: 0|1
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|0|1  (1 = error, 0 = no error)|

# Remarks:

This command is designed to be called from the ADOxx evaluation component.

# See Also:  

[LOCK_SHELL](lock_shell.html "LOCK_SHELL")  


Example:

