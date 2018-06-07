---
layout: commandcall
category: CommandCall
title: "TLB_CREATE"
tags: 1.3 1.5
---

This command creates a new internal TreeListBox but does not show it yet. To show the dialog, you have to call TLB_SHOW afterwards.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" TLB_CREATE	title:strValue
							[ oktext:strValue ] [ canceltext:strValue ]
							[ boxtext:strValue ] [ button-w:intValue ]
							[ no-cancel:intValue ] [ no-help:intValue ]
							[ x:intValue ] [ y:intValue ]
							[ w:intValue ] [ h:intValue ]
							[ sizeable:boolValue ]
							[ max-w:intValue ] [ max-h:intValue ]
							[ min-w:intValue ] [ min-h:intValue ]
							[ searchable:intValue ] [ sorted:intValue ]
							[ flat:intValue ] [ columns:intValue ]
							[ multi-sel:intValue ] [ no-child-sel:intValue ]
							[ no-parent-sel:intValue ]
							[ checklistbox:intValue ]
							[ setdblclick:intValue ]
							[ okbutton-enabled:intValue ]
							[ parentid:intValue ] [ is-parent:boolValue ]
							[ bitmap:strValue ] [ bitmap2:strValue ]

  # -->RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`title`|strValue, specifies the title of the dialog.|
|`oktext`|strValue, specifies the text for the OK-Button. Default is "OK".|
|`canceltext`|strValue, specifies the text for the Cancel-Button. Default is "Abbrechen" or "Cancel" (depending on the language of your OS).|
|`boxtext`|strValue, specifies the title text for the TreeListBox (the text which is displayed above the upper left corner of the TLB).|
|`button-w`|intValue, specifies the width of the buttons (in logical/appfont coordinates).|
|`no-cancel`|intValue, specifies that no Cancel-Button should be displayed, if the value is 1.|
|`no-help`|intValue, specifies that no Help-Button should be displayes if the value is 1.|
|`x`|intValue, specifies the startup x position of the dialog (in logical/appfont coordinates, relative to the parent window). Must be used together with parameter y.|
|`y`|intValue, specifies the startup y position of the dialog (in logical/appfont coordinates, relative to the parent window). Must be used together with parameter x.|
|`w`|intValue, specifies the startup width of the dialog (in logical/appfont coordinates). Must be used together with parameter h.|
|`h`|intValue, specifies the startup height of the dialog (in logical/appfont coordinates). Must be used together with parameter w.|
|`sizeable`|boolValue, has to be set to 0 if the dialog shall be of fixed size. The default value is 1, which means that the dialog is sizeable.|
|`max-w`|intValue, specifies the maximum width to which the user can resize the dialog (in logical/appfont coordinates). Must be used together with parameter max-h.|
|`max-h`|intValue, specifies the maximum height to which the user can resize the dialog (in logical/appfont coordinates). Must be used together with parameter max-w.|
|`min-w`|intValue, specifies the minimum width to which the user can resize the dialog (in logical/appfont coordinates). Must be used together with parameter min-h.|
|`min-h`|intValue, specifies the minimum height to which the user can resize the dialog (in logical/appfont coordinates). Must be used together with parameter min-w.|
|`searchable`|intValue, specifies that the user can search the entries of the TreeListBox via a popup menu entry if the value is 1.|
|`sorted`|intValue, specifies that the entries in the TreeListBox are sorted alphabetically if the value is 1.|
|`flat`|intValue, specifies that a TreeListBox cannot have any child entries if the value is 1.|
|`columns`|intValue, specifies the number of columns the TLB has. The default values is 1. The maximum number of columns is 16.|
|`multi-sel`|intValue, specifies that the user can select more than 1 entry by using Ctrl or Shift.|
|`no-child-sel`|intValue, specifies that the user cannot select any child entries.|
|`no-parent-sel`|intValue, specifies that the user cannot select any parent entries.|
|`checklistbox`|intValue, specifies that it will be a flat list with checkboxes on the left side.|
|`setdblclick`|intValue, specifies that if the user double clicks an item the dialog is closed with endbutton = "OK".|
|`okbutton-enabled`|intValue, specifies the initial ok button state (enabled or not). This is of course only true, if after TLB_CREATE no select command is called, before showing the TreeListBox. Default is to have the ok button disabled (if initially nothing is selected). Use okbutton-enabled:1 to allow clicking on the ok button without any selection made.|
|`parentid`|intValue|
|`is-parent`|boolValue|
|`bitmap`|strValue|
|`bitmap2`|strValue|

# Returns:  

|`ecode`|intValue, as follows 0 = no error occured, 1 = user canceled dialog, 2 = you have to call TLB_CREATE before calling this function, 3 = an argument is missing, 4 = you passed an invalid ID|

# Remarks:

If you use searchable:1 the flag checklistbox is ignored  
If you use checklistbox:1 the flags multi-sel, no-child-sel, no-parent-sel, sorted, flat and searchable are ignored. It is always flat, NOT sorted, NOT searchable and you can select all entries!

If you use TLB_CREATE and TLB_SHOW in conjunction with MSGWIN, take care to avoid the following order of AdoScript commands,  
as this will crash the ADOxx Modelling Toolkit

1. MSGWIN  
2. TLB_CREATE  
3. MSGWIN hide  
4. TLB_SHOW

The crash occurs as the parent of the TreeListBox (MSGWIN) does not exist anymore when the TreeListBox is shown.

# See Also:  

[TLB_ADD_BUTTON](tlb_add_button.html "TLB_ADD_BUTTON")  
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

# create the main TreeListBox with all its parameters
CC "AdoScript" TLB_CREATE title:"My title" oktext:"Close" canceltext:"No way!"
        boxtext:"These are my entries" no-help:1 button-w:60
        max-w:500 max-h:367 min-w:200 min-h:150 checklistbox:1

# insert some entries (as you like - ID should be unique)
CC "AdoScript" TLB_INSERT id:1 text:"Do this"
CC "AdoScript" TLB_INSERT id:2 text:"Do that"

# select the first entry (here: check it)
CC "AdoScript" TLB_SELECT id:1 select:1

# and finally show it
CC "AdoScript" TLB_SHOW
IF (ecode = 0) {
    CC "AdoScript" INFOBOX ("Selected ids: " + selectedids + "\n" +
                            "You pushed the following button: " + endbutton)
} ELSE {
    CC "AdoScript" INFOBOX ("You cancelled the dialog!")
}

{% endraw %}
```
{: .line-numbers}

