---
layout: commandcall
category: CommandCall
title: "INSERT_MENU_ITEM"
tags: 1.3 1.5
---

INSERT_MENU_ITEM creates a new menu item and inserts it into a component's menu.

# Syntax:  

```adoscript
{% raw %}
CC "Application" INSERT_MENU_ITEM component:Component item:strValue
								[ pos:ItemPos ] [ bitmap:strValue ]
								{ AdoScript }

Component :		"acquisition" | "modeling" | "analysis" |
				"simulation" | "evaluation" | "importexport" | 
				"all" .

ItemPos :		intValue | before:strValue | after:strValue .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`component`|strValue, name of the component as displayed in the list above.|
|`item`|strValue, contains the complete path of the menu item which shall be inserted. The items of that path are separated by "\t", like in "Model\tOpen...". All items before the last one must already exist. To create a new (sub)menu, at first the parent item of that (sub)menu has to be created. A separator can be inserted by using "-" as item name.|
|`pos`|intValue, the absolute position of the icon. m position can be specified with pos as an absolute value or relatively to an existing item. To insert an item before an existing item, you have to specify the before modifier, like in pos:before:"Item #3". With the after modifier an item is inserted after an existing item, e.g. pos:after:"Item #5".|
|`bitmap`|strValue, path of the imageto be displayed|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

A menu item can be inserted in one of the six ADOxx component menus, e.g. component:"modeling", or into all these menus at once (component:"all").

The (optional) icon image is loaded from the file specified with bitmap. The image may be of any graphics format. However, the recommended format is PNG with alpha channel (allowing semi-transparet pixels).

The specified AdoScript is the code which is executed when the user selects the menu item. To avoid conflicts/confusion with variables of the current script (the one which calls INSERT_MENU_ITEM) it is recommended to simply call a global procedure here.

# See Also:  

[REMOVE_MENU_ITEM](remove_menu_item.html "REMOVE_MENU_ITEM")  
[REMOVE_ALL_SUB_MENU_ITEMS](remove_all_sub_menu_items.html "REMOVE_ALL_SUB_MENU_ITEMS")  


Example 1:

```adoscript
{% raw %}

# Create a new item which will get a submenu
CC "Application" INSERT_MENU_ITEM
    component:"modeling" item:"My tools"
# First item "Tool #1" of the submenu
CC "Application" INSERT_MENU_ITEM
    component:"modeling" item:"My tools\tTool #1..."
{
    CC "AdoScript" INFOBOX "Tool #1"
}
# Second item "Tool #2" of the submenu
CC "Application" INSERT_MENU_ITEM
    component:"modeling" item:"My tools\tTool #2..."
{
    CC "AdoScript" INFOBOX "Tool #2"
}
# Third item "Tool #2" between "Tool #1" and "Tool #2"
CC "Application" INSERT_MENU_ITEM
    component:"modeling" item:"My tools\tTool #3..." pos:before:"Tool #2"
{
    CC "AdoScript" INFOBOX "Tool #3"
}

{% endraw %}
```
{: .line-numbers}

