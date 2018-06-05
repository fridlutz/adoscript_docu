---
layout: commandcall
category: CommandCall
title: "SET_EXPR_TEXT"
tags: 1.3 1.5
---

The command SET_EXPR_TEXT sets the formula of an EXPRESSION attribute.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_EXPR_TEXT objid:intValue attrid:intValue expr:strValue

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object|
|`attrid`|intValue, the ID of the attribute|
|`expr`|strValue, the value of the expression|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  

[GET_EXPR_TEXT](get_expr_text.html "GET_EXPR_TEXT")  


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
      CC "AdoScript" ERRORBOX ("Error in GET_EXPR_TEXT for object.")
      EXIT
    }

# let the user enter a new expression
    CC "AdoScript" EDITBOX text:(expr) title:"Enter an expression:" oktext:"Do it!"
    IF (endbutton != "ok")
    {
      CC "AdoScript" ERRORBOX ("You should not cancel that dialog!")
      EXIT
    }
  
# set new expression
    CC "Core" SET_EXPR_TEXT objid:(VAL firstselected) attrid:(VAL id) expr:(text)
    IF (ecode!=0)
    {
      CC "AdoScript" ERRORBOX ("Error in SET_EXPR_TEXT!")
    }
    
    CC "AdoScript" INFOBOX ("Replaced expression successfully. Check it yourself!")
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
- show EDITBOX for user to change expression  
- SET_EXPR_TEXT with new expression "text" from EDITBOX  
