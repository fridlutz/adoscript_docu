---
layout: commandcall
category: CommandCall
title: "TLB_SELECT"
tags: 1.3 1.5
---

This command can be used to manually select an entry in the TreeListBox.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_SELECT id:intValue [parentid:intValue] [select:[0|1]]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|intValue, specifies the unique ID of the entry to be selected.|
|`parentid`|intValue, specifies the ID of the parent of the entry to be selected. This may be helpful if some child entries do not have unique IDs.|
|`select`|[0|1], specifies whether the entry should be selected (value = 1) or deselected (value = 0).|

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 1 = user canceled dialog, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|

# Remarks:



# See Also:  

[TLB_ADD_BUTTON](tlb_add_button.html "TLB_ADD_BUTTON")  
[TLB_CREATE](tlb_create.html "TLB_CREATE")  
[TLB_EXPAND](tlb_expand.html "TLB_EXPAND")  
[TLB_EXPAND_ALL](tlb_expand_all.html "TLB_EXPAND_ALL")  
[TLB_EXPAND_TO](tlb_expand_to.html "TLB_EXPAND_TO")  
[TLB_INSERT](tlb_insert.html "TLB_INSERT")  
[TLB_REMOVE](tlb_remove.html "TLB_REMOVE")  
[TLB_SELECT_ALL](tlb_select_all.html "TLB_SELECT_ALL")  
[TLB_SHOW](tlb_show.html "TLB_SHOW")  


Example:

