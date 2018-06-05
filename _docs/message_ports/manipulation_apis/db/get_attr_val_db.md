---
layout: commandcall
category: CommandCall
title: "GET_ATTR_VAL_DB"
tags: 1.3 1.5
---

GET_ATTR_VAL_DB returns an attribute value. The queried object can be an instance (model, modeling object, connector, record row, attribute profile) or a class. In any case this command directly fetches the value in the database (independent of the load state of the object).

If no value is found in the database for the given object, the default value of the attribute is returned.

# Syntax:  

```adoscript
{% raw %}
CC "DB"	GET_ATTR_VAL_DB	objid:id attrid:id
						[ as-string ] [ format:strValue ] 
						[ sep:strValue ] [ core-value ] 

#--> RESULT ecode:intValue 
			val:anyValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id, the ID of the attribue|
|`attrid`|id, the ID of the instance or class|
|`as-string`|modifier, if specified, **val** is always of type string, no matter what type the attribute is. Otherwise **val** is of (LEO) type real for DOUBLE attributes, of type integer for INTEGER attributes, of type time for TIME attributes. Other attribute types than DOUBLE, INTEGER and TIME are returned as string anyway.|
|`format`|strValue, if the attribute is of type INTERREF and format is specified, val becomes the format string value for each single reference with the following replacements: %o by object name, %c by class name, %m by model name, %t by model type.|
|`sep`|strValue, the separation of multiple references can be specified with the sep string value. Default is " " (blank, which is not expedient in most cases).|
|`core-value`|modifier, if specified, the internal content of an attribute is returned. Otherwise, the result is the UI representation of the attribute value. For EXPRESSION attributes, the UI representation is the last evaluated value. core-value is needed where an attribute value shall be copied to another instance or be exported to a format which allows a later reimport. Also for attributes of type INTERREF the option core-value applies, it then does not yield a formatted value, but the internal LEO string ("REF ...")!|

# Returns:  

|`ecode`|intValue|
|`val`|anyValue|

# Remarks:

This command also works if attrid is CORE_INSTANCENAME, i.e. the name of an object is fetched

# See Also:



Example:  

