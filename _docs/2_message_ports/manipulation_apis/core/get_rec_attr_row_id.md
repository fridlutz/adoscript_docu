---
layout: commandcall
category: CommandCall
title: "GET_REC_ATTR_ROW_ID"
tags: 1.3 1.5
---

The command GET_REC_ATTR_ROW_ID returns the core id of row index in the specified RECORD attribute.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_REC_ATTR_ROW_ID objid:intValue attrid:intValue index:intValue

#-->RESULT ecode:intValue rowid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object|
|`attrid`|intValue, the ID of the attribute|
|`index`|intValue, the row index. The parameter index has the domain [ 1 .. n ]|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`rowid`|intValue, the core ID of the row.|

# Remarks:



# See Also:  

[ADD_REC_ROW](add_rec_row.html "ADD_REC_ROW")  
[MOVE_RECORD_ROW](move_record_row.html "MOVE_RECORD_ROW")  
[REMOVE_REC_ROW](remove_rec_row.html "REMOVE_REC_ROW")  
[GET_REC_CLASS_ID](get_rec_class_id.html "GET_REC_CLASS_ID")  
[GET_REC_ATTR_ROW_COUNT](get_rec_attr_row_count.html "GET_REC_ATTR_ROW_COUNT")  
[GET_OWNER_OBJ_OF_REC_ROW](get_owner_obj_of_rec_row.html "GET_OWNER_OBJ_OF_REC_ROW")  
[GET_ALL_REC_ATTR_ROW_IDS](get_all_rec_attr_row_ids.html "GET_ALL_REC_ATTR_ROW_IDS")  
[GET_RECORD_MULTIPLICITY](get_record_multiplicity.html "GET_RECORD_MULTIPLICITY")  


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

# check for type "RECORD"
  IF ((attrtype) = "RECORD")
  {
# get attribute name
    CC "Core" GET_ATTR_NAME attrid:(VAL id)

# here we get the row count
    CC "Core" GET_REC_ATTR_ROW_COUNT objid:(VAL firstselected) attrid:(VAL id)

    IF ((ecode)!=0)
    {
      CC "AdoScript" ERRORBOX ("An error occured in attribute "+(attrname))
      EXIT
    }

    IF ((count)=0)
    {
      CC "AdoScript" ERRORBOX ("Attribute \""+(attrname)+"\" contains no rows!")
      EXIT
    }

# get row id of first entry
    CC "Core" GET_REC_ATTR_ROW_ID objid:(VAL firstselected) attrid:(VAL id) index:1

# show actual row count
    CC "AdoScript" INFOBOX ("Attribute \""+(attrname)+"\" Row ID: "+(STR rowid))
    EXIT
  }
}
CC "AdoScript" ERRORBOX ("No attributes of type RECORD found!")

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
- check for attribute type RECORD  
- get attribute name  
- GET_REC_ATTR_ROW_COUNT  
- check if successful  
- check if rows exists  
- GET_REC_ATTR_ROW_ID  
- check if successful  
- show row id and exit

- if no attributes of type RECORD were found: Report error

