---
layout: commandcall
category: CommandCall
title: "INSERT_CONTEXT_MENU_ITEM"
tags: 1.3 1.5
---

INSERT_CONTEXT_MENU_ITEM inserts a new (custom) menu item into a context menu.

# Syntax:  

```adoscript
{% raw %}
CC "Application" INSERT_CONTEXT_MENU_ITEM context:Context 
										item:strValue
										[ pos:strValue ] 

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
|`pos`|strValue, specifies the position(s) of the item (or item path parts). Like at context, TAB characters are used as separators. So pos:"2\t0" means, that for the first part of the item path the insertion shall be made behind the second already existing item, while the new child item shall be inserted at the beginning of the submenu. An empty insert position value means "append". Position values are ignored for already existing superitems.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:

An item position can also be specified relatively to an existing item. You do that by writing the item name with a prefix "&lt;" or "&gt;". For example, "&lt;Cut" means "insert before item 'Cut' ", "&gt;Copy" means "insert after item 'Copy' ".

# See Also:  

[REMOVE_CONTEXT_MENU_ITEM](remove_context_menu_item.html "REMOVE_CONTEXT_MENU_ITEM")  
[REMOVE_ALL_SUB_CONTEXT_MENU_ITEMS](remove_all_sub_context_menu_items.html "REMOVE_ALL_SUB_CONTEXT_MENU_ITEMS")  


Example 1:

```adoscript
{% raw %}

# Create submenu "Test" with items "One", separator, "Two" 
CC "Application" INSERT_CONTEXT_MENU_ITEM
    context:"drawingarea.general" item:"Test\tOne"
CC "Application" INSERT_CONTEXT_MENU_ITEM
    context:"drawingarea.general" item:"Test\t-"
CC "Application" INSERT_CONTEXT_MENU_ITEM
    context:"drawingarea.general" item:"Test\tTwo"
# Insert "Three" before "Two"
CC "Application" INSERT_CONTEXT_MENU_ITEM
    context:"drawingarea.general" item:"Test\tThree" pos:"\t<Two"

{% endraw %}
```
{: .line-numbers}

