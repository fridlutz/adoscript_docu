---
layout: commandcall
category: CommandCall
title: "TLB_SHOW"
tags: 1.3 1.5
---

This command is used to finally show the TreeListBox.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_SHOW

# --> RESULT ecode:intValue selectedids:idlist [ endbutton:strValue ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 1 = user canceled dialog, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|
|`selectedids`|idlist, contains a space separated list of all entries the user selected.|
|`endbutton`|strValue, contains the name of the pressed button (Default buttons have the names "ok" and "help").|

# Remarks:

The variable endbutton is only returned if the dialog was not cancelled! If the user pressed the "X" on the upper right side of the dialog, or if he  
pressed Escape, ecode is set to 1 and endbutton is empty.

You have to insert (using TLB_INSERT) all entries before calling this command!

# See Also:  

[TLB_CREATE](tlb_create.html "TLB_CREATE")  
[TLB_EXPAND](tlb_expand.html "TLB_EXPAND")  
[TLB_EXPAND_ALL](tlb_expand_all.html "TLB_EXPAND_ALL")  
[TLB_EXPAND_TO](tlb_expand_to.html "TLB_EXPAND_TO")  
[TLB_INSERT](tlb_insert.html "TLB_INSERT")  
[TLB_REMOVE](tlb_remove.html "TLB_REMOVE")  
[TLB_SELECT](tlb_select.html "TLB_SELECT")  
[TLB_SELECT_ALL](tlb_select_all.html "TLB_SELECT_ALL")  
[TLB_SHOW](tlb_show.html "TLB_SHOW")  


Example:

