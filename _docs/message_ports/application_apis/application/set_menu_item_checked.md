---
layout: commandcall
category: CommandCall
title: "SET_MENU_ITEM_CHECKED"
tags: 1.3 1.5
---

SET_MENU_ITEM_CHECKED sets the checked mode of an item in a component's menu tree.

# Syntax:  

```adoscript
{% raw %}
CC "Application" SET_MENU_ITEM_CHECKED 	component:Component item:strValue
										checked: 0|1.

Component :		"acquisition" | "modeling" | "analysis" |
				"simulation" | "evaluation" | "importexport" | 
				"all" .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`component`|strValue, name of the component as displayed in the list above.|
|`item`|strValue, contains the complete path of the menu item which shall be inserted. The items of that path are separated by "\t", like in "Model\tOpen...". All items before the last one must already exist. To create a new (sub)menu, at first the parent item of that (sub)menu has to be created. A separator can be inserted by using "-" as item name.|
|`checked`|0|1|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  

[INSERT_MENU_ITEM](insert_menu_item.html "INSERT_MENU_ITEM")  
[SET_MENU_ITEM_ENABLED](set_menu_item_enabled.html "SET_MENU_ITEM_ENABLED")  


Example 1:

```adoscript
{% raw %}

CC "Application" SET_MENU_ITEM_CHECKED
    component:"modeling" item:"Model\tNew..." checked:1

{% endraw %}
```
{: .line-numbers}

