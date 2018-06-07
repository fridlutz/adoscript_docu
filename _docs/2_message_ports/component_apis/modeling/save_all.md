---
layout: commandcall
category: CommandCall
title: "SAVE_ALL"
tags: 1.3 1.5
---

SAVE_ALL saves all currently opened model in the modeleditor.

# Syntax:  

```adoscript
{% raw %}
ModelCloseAll :	SAVE_ALL [ quiet ].


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`quiet`|modifier|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if save worked, to 1 if an error occured.|


# Remarks:

When passing the argument quiet, no messages, error boxes etc. will be shown while saving the models.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SAVE_ALL


{% endraw %}
```
{: .line-numbers}
Saves all currently opened models.

