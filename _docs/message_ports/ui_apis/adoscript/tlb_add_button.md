---
layout: commandcall
category: CommandCall
title: "TLB_ADD_BUTTON"
tags: 1.3 1.5
---

This command is used to add another button to the dialog.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_ADD_BUTTON text:strValue 
								name:strValue 
								[ index:intValue] 
								[ disable_if_no_selection:[0|1] ]

# -->	RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`text`|strValue, specifies the text to be displayed on the user interface.|
|`name`|strValue, specifies the internal name of the button, which will be returned in the variable endbutton of the command TLB_SHOW when the button is pressed.|
|`index`|intValue, specifies the index of the button. If no index is passed, the button is appended at the end. The first valid value is 1, since the OK button must always be the first button.|
|`disable_if_no_selection`|0|1, specifies whether the button should be disabled if no entry is selected.|

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 1 = user canceled dialog, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|

# Remarks:

You have to call this command before calling TLB_SHOW.

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


Example 1:

```adoscript
{% raw %}

# create the main TreeListBox with all it's parameters :)
CC "AdoScript" TLB_CREATE title:"My title" oktext:"Close" canceltext:"No way!" boxtext:"These are my entries" no-help:1 button-w:60 max-w:500 max-h:367 min-w:200 min-h:150 checklistbox:1

# insert some entries (as you like - ID should be unique!)
CC "AdoScript" TLB_INSERT id:1 text:"Do this"
CC "AdoScript" TLB_INSERT id:2 text:"Do that"

# select the first entry (here: check it)
CC "AdoScript" TLB_SELECT id:1 select:1

# add a new button between OK and cancel
CC "AdoScript" TLB_ADD_BUTTON name:"bt1" text:"Click me" index:1

# add a new button at the end and disable it if nothing is selected
CC "AdoScript" TLB_ADD_BUTTON name:"bt2" text:"Click me2" disable_if_no_selection:1

# and finally show it!
CC "AdoScript" TLB_SHOW
IF (ecode = 0)
{
  CC "AdoScript" INFOBOX ("Selected ids: " + selectedids + "\nYou pressed the following button: " + endbutton)
}
ELSE
{
  CC "AdoScript" INFOBOX ("You cancelled the dialog!")
}

{% endraw %}
```
{: .line-numbers}

