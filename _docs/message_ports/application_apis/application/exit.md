---
layout: commandcall
category: CommandCall
title: "EXIT (Application)"
tags: 1.3 1.5
---

With the command EXIT the application is terminated without querying the user first.

# Syntax:  

```adoscript
{% raw %}
CC "Application" EXIT
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

This command works both in the Development Toolkit and in the Modelling Toolkit.

# See Also:  

[CLOSE](close.html "CLOSE")  


Example 1:

Terminates the application. The user is not asked.  
```adoscript
{% raw %}

CC "Application" EXIT

{% endraw %}
```
{: .line-numbers}


