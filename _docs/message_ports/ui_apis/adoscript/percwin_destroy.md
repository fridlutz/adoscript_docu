---
layout: commandcall
category: CommandCall
title: "PERCWIN_DESTROY"
tags: 1.3 1.5
---

PERCWIN_DESTROY deletes a previously created percentage window (See PERCWIN_CREATE for details).

# Syntax:  

```adoscript
{% raw %}
	CC "AdoScript" PERCWIN_DESTROY
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

PERCWIN_DESTROY does not return a result.

# See Also:  

[PERCWIN_IS_CANCELED](percwin_is_canceled.html "PERCWIN_IS_CANCELED")  
[PERCWIN_CREATE](percwin_create.html "PERCWIN_CREATE")  
[PERCWIN_SET](percwin_set.html "PERCWIN_SET")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" PERCWIN_CREATE title:"Fortschritt:"
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

