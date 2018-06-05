---
layout: commandcall
category: CommandCall
title: "SYSTEM"
tags: 1.3 1.5
---

SYSTEM executes a command in the operating system's environment.

# Syntax:  

```adoscript
{% raw %}
SYSTEM	strExpr [ with-console-window ] [ hide ] [ result:varName ]
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`<main_parameter>`|strExpr, the command to be executed|
|`with-console-window`|modifier, if specified, a shell window will appear, otherwise not.|
|`hide`|modifier, if specified, it means that the shell window (if existing) is not activated, i.e. it will appear "in the background".|
|`result`|varName, the result is assigned to an AdoScript variable with this name.|

# Returns:  



# Remarks:

The call is synchronous, i.e. the AdoScript process waits until the called command is terminated.

# See Also:  

[START](start.html "START")  


Example 1:

Let the user edit a file  
```adoscript
{% raw %}

SYSTEM ("notepad " + filename)

{% endraw %}
```
{: .line-numbers}

Example 1:

If you want to use features of the command shell, instead of "command" you have to write "cmd /c command". Features of the command shell are built-in commands like del and writing output to a file using &gt;filename  
```adoscript
{% raw %}

SYSTEM ("cmd /c del " + filename) result:rc
IF (rc != 0) ...

{% endraw %}
```
{: .line-numbers}

