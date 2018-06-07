---
layout: commandcall
category: CommandCall
title: "GET_ALL_ATTRS_OF_TYPE"
tags: 1.3 1.5
---

GET_ALL_ATTRS_OF_TYPE returns a list of attribute ids (separated by spaces) of a certain attribute type.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_ATTRS_OF_TYPE classid:intValue attrtype:strValue


#-->RESULT ecode:intValue attrids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|intValue, the parameter classid specifies the ID of the class of which you want to have the attributes.|
|`attrtype`|strValue|

# Returns:  

|`ecode`|intValue, if the function is successful, the result variable ecode is set to 0.|
|`attrids`|strValue|

# Remarks:

The parameter attrtype specifies the type of the attribute. It can be one of the following values:  
INTEGER  
DOUBLE  
STRING  
DISTRIBUTION  
TIME  
ENUMERATION  
ENUMERATIONLIST  
LONGSTRING  
PROGRAMCALL  
INTERREF  
EXPRESSION  
RECORD  
ATTRPROFREF  
DATE  
DATETIME  
CLOB



# See Also:  



Example:

