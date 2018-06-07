---
layout: commandcall
category: CommandCall
title: "START"
tags: 1.3 1.5
---

START starts an application in the operating systems's environment.

# Syntax:  

```adoscript
{% raw %}
START strExpr [ cmdshow: showmaximized | showminimized | showminnoactive | shownormal ]
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`<main_parameter>`|strExpr, the application to be started|
|`cmdshow`|strValue, specifies the initial state of the application's main window.|

# Returns:  



# Remarks:

The call is asynchronous, i.e. the AdoScript process continues immediately while the called program is running parallel.

# See Also:  

[SYSTEM](system.html "SYSTEM")  


Example 1:

Starting notepad  
```adoscript
{% raw %}

START ("notepad " + filename) cmdshow:showmaximized

{% endraw %}
```
{: .line-numbers}

starts notepad.exe as a maximized window.  
