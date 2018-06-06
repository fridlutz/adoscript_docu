---
layout: commandcall
category: CommandCall
title: "INFOBOX"
tags: 1.3 1.5
---

Is a command call of the message port "Core" and returns name, type, library and access information about a model.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" INFOBOX strValue [ title: strValue ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main parameter>`|strValue, the text displayed in the message window (string)|
|`title`|strValue, custom title of the message window (string)|

# Returns:  

none

# Remarks:

INFOBOX opens a message window displaying some text and waits for the user to press the "Ok" button. The text to be displayed is set with strValue. The window title can be set with title. After the user clicks "Ok", the message window closes and the execution of the adoscript is resumed.


# See Also:  

[EDITBOX](editbox.html "EDITBOX")  
[MSGWIN](msgwin.html "MSGWIN")  
[VIEWBOX](viewbox.html "VIEWBOX")  
[ERRORBOX](errorbox.html "ERRORBOX")  
[WARNINGBOX](warningbox.html "WARNINGBOX")  
[QUERYBOX](querybox.html "QUERYBOX")  


Example 1:

```adoscript
{% raw %}
CC "AdoScript" INFOBOX "Warning! Warning! \nCarefully read this information and then click Ok."

SET variable:"World"
CC "AdoScript" INFOBOX ("Hello " + variable + "!") title:"My First AdoScript Program!"

SET anumber:2001
CC "AdoScript" INFOBOX ("This example was written in the year " + STR anumber)

{% endraw %}
```
{: .line-numbers}

Displays some messages. Below is the second message box.

![](/images/INFOBOX.png)

