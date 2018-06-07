---
layout: commandcall
category: CommandCall
title: "EXEC_PRTSETUP_DLG"
tags: 1.3 1.5
---

The command EXEC_PRTSETUP_DLG executes the printer setup dialog.

# Syntax:  

```adoscript
{% raw %}
SEND "EXEC_PRTSETUP_DLG" to:"Application" answer:button

#--> RETURN strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

strValue

# Remarks:

This command call can only be used with the SEND keyword.

# See Also:  



Example 1:

```adoscript
{% raw %}
Opening the printer setup dialog

SEND "EXEC_PRTSETUP_DLG" to:"Application" answer:button
IF (button = "OK")
{
   CC "AdoScript" INFOBOX "Yeah! The user closed the printer dialog with the OK button!"
}

{% endraw %}
```
{: .line-numbers}

![](/images/EXEC_PRTSETUP_DLG.png)
