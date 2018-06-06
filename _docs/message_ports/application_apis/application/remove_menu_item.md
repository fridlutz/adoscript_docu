---
layout: commandcall
category: CommandCall
title: "REMOVE_MENU_ITEM"
tags: 1.3 1.5
---

REMOVE_MENU_ITEM removes a menu item from a component's menu bar or from a popup menu of a component's menu bar.

# Syntax:  

```adoscript
{% raw %}
CC "Application" REMOVE_MENU_ITEM	component:Component item:strValue

Component :		"acquisition" | "modeling" | "analysis" |
				"simulation" | "evaluation" | "importexport" | 
				"all" .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`component`|strValue, name of the component as displayed in the list above.|
|`item`|strValue, contains the path to the menu item which shall be removed. The items of that path are separated by "\t", like in "Model\tOpen...". An item string without "\t" (e.g. "Model") means that a top-level item of a component's menu bar shall be removed.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  

[INSERT_MENU_ITEM](insert_menu_item.html "INSERT_MENU_ITEM")  
[REMOVE_ALL_SUB_MENU_ITEMS](remove_all_sub_menu_items.html "REMOVE_ALL_SUB_MENU_ITEMS")  


Example 1:

Removing the "Model -- Open" menu item  
```adoscript
{% raw %}

CC "Application" REMOVE_MENU_ITEM
    component:"modeling" item:"Model\tOpen..."

{% endraw %}
```
{: .line-numbers}

Example 2:

Removing the complete "Bewertung" menu  
```adoscript
{% raw %}

CC "Application" debug REMOVE_MENU_ITEM component:"modeling"
    item:"Bewertung"

{% endraw %}
```
{: .line-numbers}

