---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROFCLASS_ID"
tags: 1.3 1.5
---

GET_ATTRPROFCLASS_ID determines the ID of the Attribute Profile class specified by the given name.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROFCLASS_ID apclassname:strValue . 


#-->RESULT ecode:intValue apclassid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apclassname`|strValue, the name must be passed in the parameter apclassname.|

# Returns:  

|`ecode`|intValue, the return value ecode is set to zero if function succeeded and to a non zero value else.|
|`apclassid`|intValue, the ID of the referenced AttrProf class is returned in apclassid.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get target ID
CC "Core" GET_ATTRPROFCLASS_ID apclassname:"AttrProf class"

{% endraw %}
```
{: .line-numbers}

