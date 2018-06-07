---
layout: commandcall
category: CommandCall
title: "TLB_EXPAND"
tags: 1.3 1.5
---

This command expands or collapses an entry with the given ID.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_EXPAND id:intValue [parentid:intValue] [expand:[0|1]]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|intValue, specifies the unique ID of the entry to be expanded.|
|`parentid`|intValue, specifies the ID of the parent entry of the entry to be expanded. This may be helpful if some child entries do not have unique IDs.|
|`expand`|[0|1], pecifies whether the entry should be expanded (value = 1) or collapsed (value = 0)|

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 1 = user canceled dialog, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|

# Remarks:

The parent entry of the entry to be expanded must also be expanded, otherwise this command wont work!

To expand all levels up to a certain entry, use TLB_EXPAND_TO.

# See Also:  

[TLB_ADD_BUTTON](tlb_add_button.html "TLB_ADD_BUTTON")  
[TLB_CREATE](tlb_create.html "TLB_CREATE")  
[TLB_EXPAND_ALL](tlb_expand_all.html "TLB_EXPAND_ALL")  
[TLB_EXPAND_TO](tlb_expand_to.html "TLB_EXPAND_TO")  
[TLB_INSERT](tlb_insert.html "TLB_INSERT")  
[TLB_REMOVE](tlb_remove.html "TLB_REMOVE")  
[TLB_SELECT](tlb_select.html "TLB_SELECT")  
[TLB_SELECT_ALL](tlb_select_all.html "TLB_SELECT_ALL")  
[TLB_SHOW](tlb_show.html "TLB_SHOW")  


Example:

