---
layout: commandcall
category: CommandCall
title: "LOCK_SHELL"
tags: 1.3 1.5
---

LOCK_SHELL locks the access to all menus and smart icons which shall be locked before executing the given evaluation.

# Syntax:

```adoscript
{% raw %}
CC "Evaluation" LOCK_SHELL sim: path-analysis | 
								volume-analysis | 
								steady-workload-analysis | 
								fixed-workload-analysis | 
								ccc-is-analysis | 
								ccc-plan-analysis
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`sim`|algorithm that will be run|

# Returns:  

|`ecode`|0|1  (1 = error, 0 = no error)|

# Remarks:

This command is designed to be called from the ADOxx evaluation component. After executing it, the evaluation component will be activated.

# See Also:  

[UNLOCK_SHELL](unlock_shell.html "UNLOCK_SHELL")  


Example 1:

```adoscript
{% raw %}

CC "Evaluation" LOCK_SHELL sim:volume-analysis

{% endraw %}
```
{: .line-numbers}

