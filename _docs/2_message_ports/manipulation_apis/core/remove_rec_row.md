---
layout: commandcall
category: CommandCall
title: "REMOVE_REC_ROW"
tags: 1.3 1.5
---

The command REMOVE_REC_ROW removes the row rowid in an attribute of type RECORD.

# Syntax:  

```adoscript
{% raw %}
CC "Core" REMOVE_REC_ROW objid:id attrid:id rowid:id

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, specifies the ID of the instance in which the change should take place.|
|`attrid`|intValue, specifies any attribute of type RECORD which is present in the given instance.|
|`rowid`|intValue, specifies a record row ID which must exist in the given attribute.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  

[ADD_REC_ROW](add_rec_row.html "ADD_REC_ROW")  
[MOVE_RECORD_ROW](move_record_row.html "MOVE_RECORD_ROW")  
[GET_REC_ATTR_ROW_ID](get_rec_attr_row_id.html "GET_REC_ATTR_ROW_ID")  
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
    
# show initial row count
    CC "AdoScript" INFOBOX ("Initial row count of attribute \""+(attrname)+"\": "+(STR count))

# get first row id (index = 1)
    CC "Core" GET_REC_ATTR_ROW_ID objid:(VAL firstselected) attrid:(VAL id) index:1

# remove a row
    CC "Core" REMOVE_REC_ROW objid:(VAL firstselected) attrid:(VAL id) rowid:(rowid)

    IF ((ecode)!=0)
    {
      CC "AdoScript" ERRORBOX ("Error removing a row from attribute \""+(attrname)+"\"")
      EXIT
    }

# get new row count
    CC "Core" GET_REC_ATTR_ROW_COUNT objid:(VAL firstselected) attrid:(VAL id)
    
# show new row count
    CC "AdoScript" INFOBOX ("Removed one row. New count: "+(STR count))
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
- show initial row count  
- REMOVE_REC_ROW  
- check if successful  
- GET_REC_ATTR_ROW_COUNT  
- show new row count and exit

- if no attributes of type RECORD were found: Report error

Example 2:

All record operations  
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

# show actual row count
    CC "AdoScript" INFOBOX ("Initial row count: "+(STR count)+". Now adding one...")

# no add one row
    CC "Core" ADD_REC_ROW objid:(VAL firstselected) attrid:(VAL id)

# again get row count
    CC "Core" GET_REC_ATTR_ROW_COUNT objid:(VAL firstselected) attrid:(VAL id)

# again show actual row count
    CC "AdoScript" INFOBOX ("New actual row count: "+(STR count))

# now we get the row id of added row
    CC "Core" GET_REC_ATTR_ROW_ID objid:(VAL firstselected) attrid:(VAL id) index:(count)
    CC "AdoScript" INFOBOX ("Position "+(STR count)+": RowID: "+(STR rowid))

# get record class id
    CC "Core" GET_REC_CLASS_ID attrid:(VAL id)
    CC "AdoScript" INFOBOX ("ClassID: "+(STR classid))

# delete row
    CC "AdoScript" INFOBOX ("Now removing added row...")
    CC "Core" REMOVE_REC_ROW objid:(VAL firstselected) attrid:(VAL id) rowid:(rowid)

# get again row count
    CC "Core" GET_REC_ATTR_ROW_COUNT objid:(VAL firstselected) attrid:(VAL id)
    CC "AdoScript" INFOBOX ("Final row count: "+(STR count))
  }
}

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
- ADD_REC_ROW  
- GET_REC_ATTR_ROW_COUNT  
- GET_REC_ATTR_ROW_ID  
- GET_REC_CLASS_ID  
- REMOVE_REC_ROW  
- GET_REC_ATTR_ROW_COUNT

