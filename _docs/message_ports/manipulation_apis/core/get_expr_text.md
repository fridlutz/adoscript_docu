---
layout: commandcall
category: CommandCall
title: "GET_EXPR_TEXT"
tags: 1.3 1.5
---

The command GET_EXPR_TEXT returns the default value of a class attribute or the value of an instance attribute, both of type EXPRESSION.

# Syntax:

For a class attribute  
```adoscript
{% raw %}
CC "Core" GET_EXPR_TEXT classid:intValue attrid:intValue

#-->RESULT ecode:intValue expr:strValue
{% endraw %}
```
{: .line-numbers}

For an instance attribute  
```adoscript
{% raw %}
CC "Core" GET_EXPR_TEXT objid:intValue attrid:intValue

#-->RESULT ecode:intValue expr:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|intValue, the id of the class|
|`objid`|intValue, the id of the object|
|`attrid`|intValue, the id of the attribute or class attribute|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`expr`|strValue, contains the string value of the specified attribute.|

# Remarks:



# See Also:  

[SET_EXPR_TEXT](set_expr_text.html "SET_EXPR_TEXT")  


Example 1:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "Select an instance first!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

# now get the classes of the connected instances
CC "Core" GET_CLASS_ID objid:(VAL firstselected)

# get all attributes of the selected class
CC "Core" GET_ALL_ATTRS classid:(classid)

# get types of attributes
FOR id in:(attrids)
{
  CC "Core" GET_ATTR_TYPE attrid:(VAL id)
  IF ((attrtype)="EXPRESSION")
  {
# get attribute value
    CC "Core" GET_EXPR_TEXT objid:(VAL firstselected) attrid:(VAL id)
    IF ((ecode)!=0)
    {
      CC "Core" GET_CLASS_NAME classid:(classid)
      CC "AdoScript" ERRORBOX ("Error in GET_EXPR_TEXT for object "+(classname)+"\"")
      EXIT
    }
# show value
    CC "AdoScript" INFOBOX ("ExprValue: \""+(expr)+"\"")

# get class default value
    CC "Core" GET_EXPR_TEXT classid:(classid) attrid:(VAL id)
    IF ((ecode)!=0)
    {
      CC "AdoScript" ERRORBOX ("Error in GET_EXPR_TEXT for class \""+(classname)+"\"")
      EXIT
    }

# show default value
    CC "AdoScript" INFOBOX ("Default Value: \""+(expr)+"\"")
    EXIT
  }
}

CC "AdoScript" ERRORBOX ("No attributes of type EXPRESSION found!")

{% endraw %}
```
{: .line-numbers}

Preparing:  
- get selected objects  
- pick first one  
- get class id  
- get all attributes  
- loop for all attributes  
- check for type EXPRESSION

Interesting:  
- GET_EXPR_TEXT for instance attribute (objid)  
- show value  
- GET_EXPR_TEXT for class default value (classid)  
- show value  
