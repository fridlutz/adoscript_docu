---
layout: commandcall
category: CommandCall
title: "REMOVE_CONTEXT_MENU_ITEM"
tags: 1.3 1.5
---

REMOVE_CONTEXT_MENU_ITEM removes a menu item from a context menu. It may be a custom (see INSERT_CONTEXT_MENU_ITEM) or a built-in menu item.

# Syntax:  

```adoscript
{% raw %}
CC "Application" REMOVE_CONTEXT_MENU_ITEM context:Context item:strValue .

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
|`item`|strValue, the menu name to be removed|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:

The meaning of the context and item parameters are the same as for the command INSERT_CONTEXT_MENU_ITEM. Built-in and custom context menu items can be removed.

# See Also:  

[INSERT_CONTEXT_MENU_ITEM](insert_context_menu_item.html "INSERT_CONTEXT_MENU_ITEM")  
[REMOVE_ALL_SUB_CONTEXT_MENU_ITEMS](remove_all_sub_context_menu_items.html "REMOVE_ALL_SUB_CONTEXT_MENU_ITEMS")  


Example 1:

Removing the item "Delete..." from the explorer's context menu  
```adoscript
{% raw %}

CC "Application" REMOVE_CONTEXT_MENU_ITEM
        context:"explorer.db" item:"Delete..."

{% endraw %}
```
{: .line-numbers}

