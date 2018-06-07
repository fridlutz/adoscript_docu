---
layout: commandcall
category: CommandCall
title: "GET_ATTR_VAL"
tags: 1.3 1.5
---

GET_ATTR_VAL returns an attribute value. The queried object can be an instance (model, modeling object, connector, record row, attribute profile) or a class.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTR_VAL objid:id AttrSpec
						[ as-string ] [ core-value ]
						[ format:strValue ] [ sep:strValue ] .


AttrSpec :	attrid:id | attrname:strValue .


#-->RESULT ecode:intValue val:anyValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`attrid`|id|
|`attrname`|strValue|
|`as-string`|modifier|
|`core-value`|modifier|
|`format`|strValue|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`val`|anyValue|

# Remarks:

The argument attrid has to be set to the ID of the attribue. Alternatively the name of an attribute can be specified with attrname. The argument objid has to be set to the ID of the instance or class.  
If as-string is specified, val is always of type string string, no matter what type the attribute is of. Otherwise val is of (LEO) type real for DOUBLE attributes, of type integer for INTEGER attributes, of type time for TIME attributes. Other attribute types than DOUBLE, INTEGER and TIME are returned as string anyway.  
If the attribute is of type INTERREF and format is specified, val becomes the format string value for each single reference with the following replacements: %o by object name, %c by class name, %m by model name, %t by model type.  
(%M, %v, %V gibt's auch noch)  
The separation of multiple references can be specified with the sep string value. Default is " " (blank, which is not expedient in most cases).  
If core-value is specified, the internal content of an attribute is returned. Otherwise, the result is the UI representation of the attribute value. For EXPRESSION attributes, the UI representation is the last evaluated value. core-value is needed where an attribute value shall be copied to another instance or be exported to a format which allows a later reimport.  
Note: When model attributes are queried, the concerned model must be loaded.

# See Also:  



Example:

