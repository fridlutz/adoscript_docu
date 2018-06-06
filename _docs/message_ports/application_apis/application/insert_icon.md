---
layout: commandcall
category: CommandCall
title: "INSERT_ICON"
tags: 1.3 1.5
---

INSERT_ICON inserts a new (custom) smart icon into a component's quick access bar.

# Syntax:  

```adoscript
{% raw %}
CC "Application"
INSERT_ICON	component:Component IconOrSep [ pos:intValue ] .

IconOrSep :	Icon | separator .

Icon :	name:strValue bitmap:strValue text:strValue .

Component :	"acquisition" | "modeling" | "analysis" |
			"simulation" | "evaluation" | "importexport" | 
			"all" .

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`component`|strValue, name of the component as displayed in the list above.|
|`pos`|intValue, the position of the icon|
|`name`|strValue, name of the icon|
|`bitmap`|strValue, path of the imageto be displayed|
|`text`|alternate text for the icon, to be displayed when hovering|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The icon image is loaded from the file specified with bitmap. The image may be of any graphics format. However, the recommended format is PNG with alpha channel (allowing semi-transparet pixels).

# See Also:  



Example 1:

Insert a new "tip of the day" icon and assign a click handler.  
```adoscript
{% raw %}

CC "Application" INSERT_ICON component:"modeling" name:"TIP"
    bitmap:"light.bmp" text:"Tip of the day"
CC "Application" SET_ICON_CLICK_HDL name:"TIP" {
    CC "AdoScript" INFOBOX "Nevermind!"
}

{% endraw %}
```
{: .line-numbers}

