---
layout: commandcall
category: CommandCall
title: "SET_ICON_CLICK_HDL"
tags: 1.3 1.5
---

SET_ICON_CLICK_HDL changes the click handler (the function which is executed on a click) of a smart icon.

# Syntax:  

```adoscript
{% raw %}
CC "Application" [ raw** ] SET_ICON_CLICK_HDL [ component:Component ] name:strValue 
											{ AdoScript } .

Component :	"acquisition" | "modeling" | "analysis" |
			"simulation" | "evaluation" | "importexport" | 
			"all" .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`component`|strValue, name of the component as displayed in the list above|
|`name`|strValue, name of the icon|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The name of a custom smart icon is the name specified at INSERT_ICON. The names of the built-in smart icons are listed in the SET_ICON_VISIBLE documentation.

The raw argument at the CC element may be of importance here! Without specifying raw, variables used in the handler are replaced by the current values of these variables. If the handler just calls a global procedure without parameters, raw is not needed.

# See Also:  

[SET_ICON_VISIBLE](set_icon_visible.html "SET_ICON_VISIBLE")  
[INSERT_ICON](insert_icon.html "INSERT_ICON")  


Example:

