---
layout: commandcall
category: CommandCall
title: "GET_ATTR_TYPE"
tags: 1.3 1.5
---

GET_ATTR_TYPE returns the type of an attribute. The id of the attribute is passed in the argument attrid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTR_TYPE	attrid:id .


#-->RESULT ecode:intValue attrtype:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attrid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`attrtype`|strValue|

# Remarks:

The return variable attrtype is set to the name of the attribute type.  
Possible values are:

Name			Type  
INTEGER			Integer  
DOUBLE			Floating point number  
STRING			Short string (max. 3,700 chars)  
DISTRIBUTION	(actually not used)  
TIME			Time  
ENUMERATION		Enumeration  
ENUMERATIONLIST	Enumeration list  
LONGSTRING		Long string (max. 32,000 chars)  
PROGRAMCALL		Program call  
INTERREF		Inter-model reference  
EXPRESSION		Expression  
RECORD			Record table  
ATTRPROFREF		Attribute profile reference  
DATE			Date  
DATETIME		Date and time  
CLOB			Character Large OBject  
(has nothing to do with a famous BVB 09 coach)


# See Also:  



Example:

