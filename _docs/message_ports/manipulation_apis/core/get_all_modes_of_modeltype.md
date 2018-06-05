---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODES_OF_MODELTYPE"
tags: 1.3 1.5
---

GET_ALL_MODES_OF_MODELTYPE returns the modi which are defined for a certain model type.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_MODES_OF_MODELTYPE modeltype:strValue [ sep:strValue ]
									[ no-modeling ] [ no-documentation ] .

#--> RESULT modenames:strValue ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue, the name of the modeltype|
|`sep`|strValue, the separator to be placed between mode names; default is " "|
|`no-modeling`|modifier|
|`no-documentation`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modenames`|strValue, a list of mode names separated by the given separator|

# Remarks:



# See Also:

