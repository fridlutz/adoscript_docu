---
layout: commandcall
category: CommandCall
title: "MSGWIN"
tags: 1.3 1.5
---

MSGWIN displays a message window containing some text.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" MSGWIN strValue

CC "AdoScript" MSGWIN hide
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main parameter>`|strValue, the text shown in the message window (string)|
|`hide`|modifier, hides the messagewindow|

# Returns:  

none

# Remarks:

When displaying the message window, the execution of adoscript does not stop but is continued. The message window can be hidden again by another call of MSGWIN with the argument hide.

Don't forget to close the messagewindow again! If the message window is still open after the adoscript finished executing, the user can not work with ADOxx until it is restarted because the message window blocks all the mouse and keyboard inputs.

You can set text with more than one line by separating each line with a '\n'.

# See Also:



Example 1:

```adoscript
{% raw %}

FOR i from:1 to:50000 {
   CC "AdoScript" MSGWIN ("Important message. Counting up to 50000: " + STR i)
}
CC "AdoScript" MSGWIN hide

{% endraw %}
```
{: .line-numbers}

Opens the message window with the text "Important message". Then some time consuming computations would take place. In the example we just open an info box so that the user has time to read the message in the message window. After the info box is closed, the message window is again hidden:

![](/images/MSGWIN.png)
