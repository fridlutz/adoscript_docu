---
layout: commandcall
category: CommandCall
title: "CLOSE (Application)"
tags: 1.3 1.5
---

With the command CLOSE, the ADOxx application is closed.

# Syntax:  

```adoscript
{% raw %}
CC "Application" CLOSE
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

First the user is asked if he really wants to close ADOxx (same as closing ADOxx in the menu).  
![](/images/CLOSE.png)

# See Also:  

[EXIT](exit.html "EXIT")  


Example 1:

Closes the application.  
```adoscript
{% raw %}

CC "Application" CLOSE

{% endraw %}
```
{: .line-numbers}

