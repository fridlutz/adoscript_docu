---
layout: commandcall
category: CommandCall
title: "GET_RECORD_MULTIPLICITY"
tags: 1.3 1.5
---

The command GET_RECORD_MULTIPLICITY retrieves the maxmimum possible number of records rows in an attribute.

# Syntax:  


```adoscript
{% raw %}
#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  

[ADD_REC_ROW](add_rec_row.html "ADD_REC_ROW")  
[MOVE_RECORD_ROW](move_record_row.html "MOVE_RECORD_ROW")  
[REMOVE_REC_ROW](remove_rec_row.html "REMOVE_REC_ROW")  
[GET_REC_ATTR_ROW_ID](get_rec_attr_row_id.html "GET_REC_ATTR_ROW_ID")  
[GET_REC_CLASS_ID](get_rec_class_id.html "GET_REC_CLASS_ID")  
[GET_REC_ATTR_ROW_COUNT](get_rec_attr_row_count.html "GET_REC_ATTR_ROW_COUNT")  
[GET_OWNER_OBJ_OF_REC_ROW](get_owner_obj_of_rec_row.html "GET_OWNER_OBJ_OF_REC_ROW")  
[GET_ALL_REC_ATTR_ROW_IDS](get_all_rec_attr_row_ids.html "GET_ALL_REC_ATTR_ROW_IDS")  


Example 1:

```adoscript
{% raw %}

SET clname:"Start"
SET aname:"Responsible"

CC "Core" GET_CLASS_ID classname:(clname)
SET clid:(classid)

IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX ("There is no such class")
  EXIT
}

CC "Core" GET_ATTR_ID classid:(clid) attrname:(aname)
SET aid:(attrid)

IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX ("There is no such attribute")
  EXIT
}

CC "Core" GET_RECORD_MULTIPLICITY attrid:(aid)

IF (multiplicity = 0)
{
  CC "AdoScript" INFOBOX ("Infinite rows are allowed")
}
ELSE
{
  CC "AdoScript" INFOBOX ("Maximum rows is " + (STR multiplicity))
}

{% endraw %}
```
{: .line-numbers}

- get all ADOxx Dynamic modeltypes  
- get all ADOxx Static modeltypes  
- get all ADOxx modeltypes  
- print 'em  
