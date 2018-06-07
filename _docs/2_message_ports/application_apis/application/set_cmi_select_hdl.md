---
layout: commandcall
category: CommandCall
title: "SET_CMI_SELECT_HDL"
tags: 1.3 1.5
---

SET_CMI_SELECT_HDL replaces the code which is executed on selection of a context menu item with an AdoScript. It may be a custom (see INSERT_CONTEXT_MENU_ITEM) or a built-in menu item.

# Syntax:  

```adoscript
{% raw %}
CC "Application" [ raw** ] SET_CMI_SELECT_HDL context:Context item:strValue { AdoScript } .

Context :	"drawingarea.general" | "drawingarea.mobject" |
			"drawingarea.connector" | "drawingarea.swimlane" |
			"modelingtable" |"explorer.db" | 
			"explorer.windows" | "startpage.thumb" .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`context`|strValue, specifies which context menu shall be modified.|
|`item`|strValue, the menu name. If the item shall be placed in a submenu, the parts of the item path are separated by TAB ("\t") characters, e.g. "New\tModelgroup...". A separator can be inserted by using "-" as item name.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The given AdoScript is executed instead of the default action when the user selects the changed menu item. In the menu handler variables context and item are preset accordingly.

Additionally the component may set some context specific variables  
Context	Variable	Value  
* "explorer.db"	: modelids, IDs of currently selected models, and mgroupids, IDs of currently selected model groups.
* "explorer.windows" : modelids, IDs of currently selected models
* "startpage.thumb"	: modelid, ID of the model for whose thumb the current menu item is executed, and mode, current start page mode ("favorites", "recent" or "opened")

In the context of a "drawingarea" event handler it is not allowed to close the related model window. Doing this will result in a crash of the application (because data is deleted which is still being accessed).

The raw argument at the CC element may be of importance here! Without specifying raw, variables used in the handler are replaced by the current values of these variables. If the handler just calls a global procedure without parameters, raw is not needed.

# See Also:  

[INSERT_CONTEXT_MENU_ITEM](insert_context_menu_item.html "INSERT_CONTEXT_MENU_ITEM")  
[REMOVE_CONTEXT_MENU_ITEM](remove_context_menu_item.html "REMOVE_CONTEXT_MENU_ITEM")  


Example 1:

Changing a built-in context menu item  
```adoscript
{% raw %}

CC "Application" raw SET_CMI_SELECT_HDL
    context:"drawingarea.mobject" item:"Delete"
{
    CC "AdoScript" INFOBOX "Deleting has been made impossible..."
}

{% endraw %}
```
{: .line-numbers}

Example 2:

Inserting a custom context menu item  
```adoscript
{% raw %}

CC "Application" INSERT_CONTEXT_MENU_ITEM
   context:"explorer.db" item:"Test"
CC "Application" raw SET_CMI_SELECT_HDL
    context:"explorer.db" item:"Test"
{
    CC "AdoScript" INFOBOX (curvars())
}

{% endraw %}
```
{: .line-numbers}

