---
layout: commandcall
category: CommandCall
title: "QUERYBOX"
tags: 1.3 1.5
---

QUERYBOX opens a message window displaying some text and waits for the user to press some button.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" QUERYBOX strValue [ title:strValue ] 
						[ ok | ok-cancel | yes-no | yes-no-cancel | retry-cancel ] 
						[ def-ok | def-cancel | def-yes | def-no | def-retry ] .

# --> RESULT endbutton:strValue
{% endraw %}
```
{: .line-numbers}
# Parameters:  

strValue
|`title`|strValue|
|`ok`|modifier|
|`ok-cancel`|modifier|
|`yes-no`|modifier|
|`yes-no-cancel`|modifier|
|`retry-cancel`|modifier|
|`def-ok`|modifier|
|`def-cancel`|modifier|
|`def-yes`|modifier|
|`def-no`|modifier|
|`def-retry`|modifier|

# Returns:  

|`endbutton`|strValue|

# Remarks:

The text to be displayed is set with strValue. The window title can be set with title. After the user clicks a button, the message window closes and the execution of the adoscript is resumed.

Depending on the type or the messagebox, different icons are displayed.

By entereing one of the arguments ok, ok-cancel, yes-no, yes-no-cancel or retry-cancel, you can specify which buttons the querybox should display. By entereing one of the arguments def-ok, def-cancel, def-yes, def-no or def-retry, you can specify which of the buttons is the default button.

The return variable endbutton contains the name of the button the user pressed (see examples).

# See Also:  

[ERRORBOX](errorbox.html "ERRORBOX")  
[WARNINGBOX](warningbox.html "WARNINGBOX")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" QUERYBOX "Choose a button..." yes-no-cancel def-cancel
CC "AdoScript" INFOBOX ("The user pressed " + endbutton)

CC "AdoScript" WARNINGBOX "Another example..." retry-cancel
CC "AdoScript" INFOBOX ("The user pressed " + endbutton)

{% endraw %}
```
{: .line-numbers}

Starts a QUERYBOX and then prints the return variable endbutton in an INFOBOX. The query box has the buttons "yes", "no" and "cancel". The default button is the "cancel" button.

Next, a WARNINGBOX is started. Available buttons are "retry" and "cancel". No default button is specified so ADOxx picks its own. After clicking a button, the result is again displayed in an INFOBOX.  
