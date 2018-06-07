---
layout: commandcall
category: CommandCall
title: "EXECUTE_PROGRAMCALL"
tags: 1.3 1.5
---

The command EXECUTE_PROGRAMCALL executes the programcall of the specified attribute of type PROGRAMCALL.

# Syntax:  

```adoscript
{% raw %}
CC "Core" EXECUTE_PROGRAMCALL objid:id attrid:id .

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the object id|
|`attrid`|intValue, the id of an attribute of type PROGRAMCALL|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success|

# Remarks:



# See Also:  



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

# check for type "PROGRAMCALL"
  IF ((attrtype) = "PROGRAMCALL")
  {
# execute the call
    CC "Core" EXECUTE_PROGRAMCALL objid:(VAL firstselected) attrid:(VAL id)
    IF ((ecode)!=0)
    {
      CC "AdoScript" ERRORBOX ("EXECUTE_PROGRAMCALL failed! "+result)
      EXIT
    }
    CC "AdoScript" INFOBOX ("Execution successful!")
    EXIT
  }
}

CC "AdoScript" ERRORBOX ("No attribute of type PROGRAMMCALL found!")

{% endraw %}
```
{: .line-numbers}

Preparing:  
- Get selected objects  
- pick first selected  
- get its class id  
- get all attributes of that class  
- loop for all attributes

Interesting:  
- check for attribute type PROGRAMMCALL  
- EXECUTE_PROGRAMMCALL  
- check for success

- if no attributes of type RECORD were found: Report error

