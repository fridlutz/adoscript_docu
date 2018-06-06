---
layout: commandcall
category: CommandCall
title: "VIEWBOX"
tags: 1.3 1.5
---

VIEWBOX opens a view box to display longer text messages.

# Syntax:

```adoscript
{% raw %}
CC "AdoScript" VIEWBOX 	text:strValue [ title:strValue ] 
						[ fontname:strValue ] [ fontheight:intValue ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`text`|strValue, the text to be displayed|
|`title`|strValue, the window title|
|`fontname`|strValue|
|`fontheight`|intValue|

# Returns:  

none

# Remarks:

The viewbox waits for the user to press the "Close" button.

After the user clicks "Close", the message window closes and the execution of the AdoScript is resumed.

# See Also:  



Example 1:

```adoscript
{% raw %}

SET longmessage:"A longer text message:\n\n"
FOR i from:1 to:100
{
   SET longmessage:(longmessage+"line no. " + STR i + ".\n")
}
CC "AdoScript" VIEWBOX text:(longmessage) title:"A longer text message:" fontheight:20

{% endraw %}
```
{: .line-numbers}

Displays some messages.

Second message box is

![](/images/VIEWBOX.png)

