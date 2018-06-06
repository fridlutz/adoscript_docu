---
layout: commandcall
category: CommandCall
title: "GET_OPENED_MODELS"
tags: 1.3 1.5
---

GET_OPENED_MODELS returns a list of all  opened modelids (separated by spaces).

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_OPENED_MODELS .


# --> RESULT ecode:intValue modelids:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the command worked, to 1 if an error occured.|
|`modelids`|strValue|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_OPENED_MODELS

{% endraw %}
```
{: .line-numbers}
Retrieves ids of all opened models.

