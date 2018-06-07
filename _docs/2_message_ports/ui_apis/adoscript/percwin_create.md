---
layout: commandcall
category: CommandCall
title: "PERCWIN_CREATE"
tags: 1.3 1.5
---

PERCWIN_CREATE creates a new percentage window.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" PERCWIN_CREATE	[ title:strValue ] [ with-second-bar:boolValue ]
								[ with-cancel-button:boolValue ] .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`title`|strValue, sets the title of the percentage window.|
|`with-second-bar`|boolValue, if true (i.e. specified alone or with a nonzero value), the percentage window is created with two progress bars, otherwise with one.|
|`with-cancel-button`|boolValue, if true (i.e. specified alone or with a nonzero value), the percentage window is created with a cancel button. The cancel button can be pushed by the user while the percentage window is visible. The "canceled" status can be retrieved with the command  CC "AdoScript"|

# Returns:  

none

# Remarks:

To set the percentage value, PERCWIN_SET has to be called.  
Only one percentage window can exist at a time. If PERCWIN_CREATE is called while another percentage window is existing, the previous one is destroyed automatically.

PERCWIN_CREATE does not return a result.

# See Also:  

[PERCWIN_IS_CANCELED](percwin_is_canceled.html "PERCWIN_IS_CANCELED")  
[PERCWIN_DESTROY](percwin_destroy.html "PERCWIN_DESTROY")  
[PERCWIN_SET](percwin_set.html "PERCWIN_SET")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" PERCWIN_CREATE title:"My percentage window"
SET step:0
FOR i from:0 to:100 by:2 {
    SET step:(step + 1)
    CC "AdoScript" PERCWIN_SET percentage:(i) text:("Step " + STR step)
    CC "AdoScript" SLEEP ms:200
}
CC "AdoScript" INFOBOX "Fertig!"
CC "AdoScript" PERCWIN_DESTROY

{% endraw %}
```
{: .line-numbers}


