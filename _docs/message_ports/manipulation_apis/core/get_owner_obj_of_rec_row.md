---
layout: commandcall
category: CommandCall
title: "GET_OWNER_OBJ_OF_REC_ROW"
tags: 1.3 1.5
---

GET_OWNER_OBJ_OF_REC_ROW returns the ID of the object which owns a specified record row.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_OWNER_OBJ_OF_REC_ROW rowid:intValue

#-->RESULT ecode:intValue objid: intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`rowid`|intValue, the ID of the row|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objid`|intValue, the ID of the object that contains the specified row|

# Remarks:

Any existing record row belongs to a certain attribute and to exactly one object with that attribute.

# See Also:

[ADD_REC_ROW](add_rec_row.html "ADD_REC_ROW")  
[MOVE_RECORD_ROW](move_record_row.html "MOVE_RECORD_ROW")  
[REMOVE_REC_ROW](remove_rec_row.html "REMOVE_REC_ROW")  
[GET_REC_ATTR_ROW_ID](get_rec_attr_row_id.html "GET_REC_ATTR_ROW_ID")  
[GET_REC_CLASS_ID](get_rec_class_id.html "GET_REC_CLASS_ID")  
[GET_REC_ATTR_ROW_COUNT](get_rec_attr_row_count.html "GET_REC_ATTR_ROW_COUNT")  
[GET_ALL_REC_ATTR_ROW_IDS](get_all_rec_attr_row_ids.html "GET_ALL_REC_ATTR_ROW_IDS")  
[GET_RECORD_MULTIPLICITY](get_record_multiplicity.html "GET_RECORD_MULTIPLICITY")  


