---
layout: commandcall
category: CommandCall
title: "SET_EXPLORER_UPDATEMODE"
tags: 1.3 1.5
---

SET_EXPLORER_UPDATEMODE allows to change the UI update behaviour of the explorer.

# Syntax:  

```adoscript
{% raw %}
CC "Explorer" SET_EXPLORER_UPDATEMODE on | off 

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|on or off; if set to "off", no UI updates will take place until the update mode is set back to "on".|

# Returns:  

|`ecode`|intValue|

# Remarks:

If set back to "on", the explorer UI is updated immediately.

If neither "on" or "off" is specified as update mode, eCode will be set to 1.  
Otherwise 0 is returned.

# See Also:  


