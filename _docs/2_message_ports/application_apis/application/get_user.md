---
layout: commandcall
category: CommandCall
title: "GET_USER"
tags: 1.3 1.5
---

The command GET_USER returns the current username.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_USER

#--> RESULT user:strValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`user`|strValue|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_USER 

{% endraw %}
```
{: .line-numbers}

