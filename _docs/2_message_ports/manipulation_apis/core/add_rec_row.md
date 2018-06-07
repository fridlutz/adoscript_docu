---
layout: commandcall
category: CommandCall
title: "ADD_REC_ROW"
tags: 1.3 1.5
---

ADD_REC_ROW adds a row to the specified RECORD attribute and returns the ID of the new row.

# Syntax:  

```adoscript
{% raw %}
CC "Core" ADD_REC_ROW objid:intValue attrid:intValue [ predrowid:intValue ]

#-->RESULT ecode:intValue rowid:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object|
|`attrid`|intValue, the ID of the attribute|
|`prerowid`|intValue, specifies the preceeding row so you can insert a new row in an existing structure. To add a row at first position pass predrowid with value "0". To add a row at the end (default) pass predrowid with value "-1".|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success. If ecode is MULTIPLICITY_EXCEEDED, then the record limit of entries has been reached.|
|`rowid`|intValue, holds the core id for the new added row.|

# Remarks:



# See Also:  

[MOVE_RECORD_ROW](move_record_row.html "MOVE_RECORD_ROW")  
[REMOVE_REC_ROW](remove_rec_row.html "REMOVE_REC_ROW")  
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
IF (objids = "") {
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
FOR id in:(attrids) {
    CC "Core" GET_ATTR_TYPE attrid:(VAL id)

    # check for type "RECORD"
    IF ((attrtype) = "RECORD") {
        # get attribute name
        CC "Core" GET_ATTR_NAME attrid:(VAL id)

        # here we get the row count
        CC "Core" GET_REC_ATTR_ROW_COUNT objid:(VAL firstselected) attrid:(VAL id)

        IF ((ecode)!=0) {
            CC "AdoScript" ERRORBOX ("An error occured in attribute "+(attrname))
            EXIT
        }
    
        # show initial row count
        CC "AdoScript" INFOBOX
                ("Initial row count of attribute \""+(attrname)+"\": "+(STR count))

        # add a row
        CC "Core" ADD_REC_ROW objid:(VAL firstselected) attrid:(VAL id)

        IF ((ecode)!=0) {
            CC "AdoScript" ERRORBOX
                    ("Error adding a row to attribute \""+(attrname)+"\"")
            EXIT
        }

        # get new row count
        CC "Core" GET_REC_ATTR_ROW_COUNT objid:(VAL firstselected) attrid:(VAL id)
    
        # show new row count
        CC "AdoScript" INFOBOX
                ("Added one row. ID: "+(STR rowid)+" Count: "+(STR count))
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
- ADD_REC_ROW  
- check if successful  
- GET_REC_ATTR_ROW_COUNT  
- show new row count and row id and exit

- if no attributes of type RECORD were found: Report error  
