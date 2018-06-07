---
layout: commandcall
category: CommandCall
title: "TLB_REMOVE"
tags: 1.3 1.5
---

Remove the given entry from the TreeListBox.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_REMOVE id:intValue [parentid:intValue]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|intValue, specifies the unique ID of the entry to be removed.|
|`parentid`|intValue, specifies the ID of the parent of the entry to be removed. This may be helpful if some child entries do not have unique IDs.|

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 1 = user canceled dialog, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|

# Remarks:

If the entry to be removed has child entries, they are removed too.

# See Also:  

[TLB_ADD_BUTTON](tlb_add_button.html "TLB_ADD_BUTTON")  
[TLB_CREATE](tlb_create.html "TLB_CREATE")  
[TLB_EXPAND](tlb_expand.html "TLB_EXPAND")  
[TLB_EXPAND_ALL](tlb_expand_all.html "TLB_EXPAND_ALL")  
[TLB_EXPAND_TO](tlb_expand_to.html "TLB_EXPAND_TO")  
[TLB_INSERT](tlb_insert.html "TLB_INSERT")  
[TLB_SELECT](tlb_select.html "TLB_SELECT")  
[TLB_SELECT_ALL](tlb_select_all.html "TLB_SELECT_ALL")  
[TLB_SHOW](tlb_show.html "TLB_SHOW")  


Example:

