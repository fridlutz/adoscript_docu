---
layout: commandcall
category: CommandCall
title: "GET_DB_NAME"
tags: 1.3 1.5
---

The command GET_DB_NAME returns the current database name you are connected to.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_DB_NAME

#--> RESULT dbname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`dbname`|strValue, the name of the current database.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_DB_NAME

{% endraw %}
```
{: .line-numbers}

