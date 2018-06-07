---
layout: commandcall
category: CommandCall
title: "SET_MENU_ITEM_HDL"
tags: 1.3 1.5
---

SET_MENU_ITEM_HDL associates an AdoScript with an existing menu item. This command can be used to replace an internal menu item handler (the functions called on menu item selection) with a custom handler.

# Syntax:  

```adoscript
{% raw %}
CC "Application" [ raw** ] SET_MENU_ITEM_HDL	component:Component item:strValue
											{ AdoScript } .

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

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The raw argument at the CC element may be of importance here! Without specifying raw, variables used in the handler are replaced by the current values of these variables. If the handler just calls a global procedure without parameters, raw is not needed.

# See Also:  



Example 1:

Replacing the handler of the "Model -- Open" menu item  
```adoscript
{% raw %}

CC "Application" raw SET_MENU_ITEM_HDL
    component:"modeling" item:"Model\tOpen..."
{
    CC "AdoScript" INFOBOX "You dont need none!"
}

{% endraw %}
```
{: .line-numbers}

