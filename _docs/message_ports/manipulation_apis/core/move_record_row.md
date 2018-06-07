---
layout: commandcall
category: CommandCall
title: "MOVE_RECORD_ROW"
tags: 1.3 1.5
---

The command MOVE_RECORD_ROW moves a record row in an RECORD attribute to another index without changing its ID!

# Syntax:  

```adoscript
{% raw %}
CC "Core" MOVE_RECORD_ROW 	modelid:intValue 
							objid:intValue 
							attrid:intValue 
							rowid:intValue 
							index:intValue

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, specifies the ID of the model in which the change should take place.|
|`objid`|intValue, specifies the ID of the instance in which the change should take place.|
|`attrid`|intValue, specifies any attribute of type RECORD which is present in the given instance.|
|`rowid`|intValue, specifies a record row ID which must exist in the given attribute.|
|`index`|intValue, specifies the new index of the row.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This index is 1-based which means, the first row has index 1, the next one has index 2, etc. If the new index is equal to the old index, nothing is done, and the ecode is set to 0.

Use ECODE_TO_ERRTEXT to convert the ecode into a string.

# See Also:  

[ADD_REC_ROW](add_rec_row.html "ADD_REC_ROW")  
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

# declare some constants (tested with BOC Test AB 1.34)
SET mname:"MoveRecordRow"
SET mtype:"Gesch�ftsproze�modell"
SET mver:"Test"
SET cname:"Proze�start"
SET iname:"Test"
SET aname:"Proze�verantwortung"

# get model ID
CC "Core" GET_MODEL_ID modelname:(mname) modeltype:(mtype) version:(mver)
SET mid:(modelid)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Unknown model"
  EXIT
}

# get class ID
CC "Core" GET_CLASS_ID classname:(cname)
SET cid:(classid)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Unknown class"
  EXIT
}

# get instance ID
CC "Core" GET_OBJ_ID modelid:(mid) classid:(cid) objname:(iname)
SET iid:(objid)
IF (ecode != 0
{
  CC "AdoScript" ERRORBOX "Unknown instance"
  EXIT
}

# get attribute ID
CC "Core" GET_ATTR_ID classid:(cid) attrname:(aname)
SET aid:(attrid)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Unknown attribute"
  EXIT
}

# get row count
CC "Core" GET_REC_ATTR_ROW_COUNT objid:(iid) attrid:(aid)
SET reccnt:(count)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Internal error - GET_REC_ATTR_ROW_COUNT failed"
  EXIT
}

# any rows present?
IF (reccnt = 0)
{
  CC "AdoScript" ERRORBOX "No record rows present"
  EXIT
}

# there must be at least 2 rows!
IF (reccnt < 2)
{
  # ask user whether he wants to make a second row
  CC "AdoScript" QUERYBOX "You need at least 2 record rows.\n\nShould I create a second row?" yes-no
  IF (endbutton = "yes")
  {
    # try to create a second row
    CC "Core" ADD_REC_ROW objid:(iid) attrid:(aid)
    IF (ecode != 0)
    {
      CC "AdoScript" ERRORBOX "Failed to add another record row"
      EXIT
    }

    # inc record row counter
    SET reccnt:(reccnt + 1)
  }
  ELSE
  {
    # I don't create anything
    EXIT
  }
}

# get ID of first row (index is 1-based !!!)
CC "Core" GET_REC_ATTR_ROW_ID objid:(iid) attrid:(aid) index:1
SET rid:(rowid)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Internal error - GET_REC_ATTR_ROW_ID failed"
  EXIT
}

# now move first row to second row
CC "Core" MOVE_RECORD_ROW modelid:(mid) objid:(iid) attrid:(aid) rowid:(rid) index:2
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Internal error - MOVE_RECORD_ROW failed"
  EXIT
}

# we did it
CC "AdoScript" INFOBOX "Success!!"

{% endraw %}
```
{: .line-numbers}

- resolve all IDs  
- check if enough record rows are present  
- move first row to second

