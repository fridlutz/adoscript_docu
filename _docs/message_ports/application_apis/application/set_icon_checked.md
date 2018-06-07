---
layout: commandcall
category: CommandCall
title: "SET_ICON_CHECKED"
tags: 1.3 1.5
---

SET_ICON_CHECKED sets the checked mode of a smart icon in a component's quick access bar.

# Syntax:  

```adoscript
{% raw %}
CC "Application" SET_ICON_CHECKED name:strValue checked: 0|1 .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

name: strValue, name of the icon
checked: 0|1 .

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|

# Remarks:

A table of predefined names is shown in the documentation of SET_ICON_VISIBLE.

# See Also:  

[SET_ICON_VISIBLE](set_icon_visible.html "SET_ICON_VISIBLE")  
[INSERT_ICON](insert_icon.html "INSERT_ICON")  


