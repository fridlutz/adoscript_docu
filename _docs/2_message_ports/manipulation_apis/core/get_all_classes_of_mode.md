---
layout: commandcall
category: CommandCall
title: "GET_ALL_CLASSES_OF_MODE"
tags: 1.3 1.5
---

GET_ALL_CLASSES_OF_MODE returns the classes which are visible in a certain mode.  


# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_CLASSES_OF_MODE 	modeltype:strValue [ variant:strValue ]
									modename:strValue .

#--> RESULT classids:strValue ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue, the name of the model type|
|`variant`|strValue, the name of the variant|
|`modename`|strValue, the name of the mode|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|
|`classids`|strValue, list of IDs of classes|

# Remarks:



# See Also:  



