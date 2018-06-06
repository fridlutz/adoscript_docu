---
layout: commandcall
category: CommandCall
title: "GET_MAX_USER_COUNT"
tags: 1.3 1.5
---

The command GET_USER returns the maximum user count that are allowed to be online.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_MAX_USER_COUNT 

#--> RESULT maxuser:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`maxuser`|intValue|

# Remarks:

The max user count is hidden in the licencenumber.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_MAX_USER_COUNT 

{% endraw %}
```
{: .line-numbers}

