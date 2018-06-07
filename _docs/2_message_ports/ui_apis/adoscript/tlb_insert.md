---
layout: commandcall
category: CommandCall
title: "TLB_INSERT"
tags: 1.3 1.5
---

Inserts a new item in the TreeListBox

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_INSERT	id:intValue text:strValue
							[ parentid:intValue] [ is-parent:boolValue]
							[ bitmap:strValue ] [ bitmap2:strValue ]

  # --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|intValue, unique identifier of the new entry|
|`text`|strValue, text to be displayed|
|`parentid`|intValue, specifies the parent entry of the new entry. This is how you create the tree-like structure. If you do not specify this parameter, the entry is inserted as a root entry.|
|`is-parent`|boolValue, 0 = The new entry is a leaf (has no subentries), 1 = The new entry is a parent (can be expanded). Parents are displayed with a folder icon.|
|`bitmap`|strValue, name of a graphics file. The graphics is used as icon for the new entry.	All common bitmap file types are supported, e.g. png, gif, bmp.	The dimensions of the bitmap should be 16x16 pixels. With other dimensions the bitmap is stretched to 16x16 automatically.|
|`bitmap2`|strValue, name of a graphics file. The graphics is used as icon for the new entry when the entry is in expanded state.|

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|

# Remarks:

If you have a multy column TLB (the parameter columns was specified at the command TLB_CREATE) you must separate the text for each column with a tab character ("\t").  
&gt; TLB_INSERT id:1 text:"Column 1\tColumn 2\tColumn 3"

# See Also:  

[TLB_ADD_BUTTON](tlb_add_button.html "TLB_ADD_BUTTON")  
[TLB_CREATE](tlb_create.html "TLB_CREATE")  
[TLB_EXPAND](tlb_expand.html "TLB_EXPAND")  
[TLB_EXPAND_ALL](tlb_expand_all.html "TLB_EXPAND_ALL")  
[TLB_EXPAND_TO](tlb_expand_to.html "TLB_EXPAND_TO")  
[TLB_REMOVE](tlb_remove.html "TLB_REMOVE")  
[TLB_SELECT](tlb_select.html "TLB_SELECT")  
[TLB_SELECT_ALL](tlb_select_all.html "TLB_SELECT_ALL")  
[TLB_SHOW](tlb_show.html "TLB_SHOW")  



Example:

