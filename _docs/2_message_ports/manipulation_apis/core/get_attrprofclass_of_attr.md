---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROFCLASS_OF_ATTR"
tags: 1.3 1.5
---

GET_ATTRPROFCLASS_OF_ATTR determines the AttrProf class which is referenced by the given attribute (attrid).

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROFCLASS_OF_ATTR attrid:intValue . 


#-->RESULT ecode:intValue apclassid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attrid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`apclassid`|intValue|

# Remarks:


The ID of the referenced AttrProf class is returned in apclassid.

returns ATTRIBUTE_NOT_EXISTING if the given attribute (attrid) does not exist  
returns WRONG_ATTRIBUTE_TYPE if the given attribute (attrid) is no AttrProfRef attribute  
returns INVALID_ATTRPROFREF_VALUE if the given attribute (attrid) has no valid AttrProf class

# See Also:  



Example:

