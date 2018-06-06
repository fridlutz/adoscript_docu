---
layout: commandcall
category: CommandCall
title: "EDITBOX"
tags: 1.3 1.5
---

EDITBOX opens a box where the user can edit text.

# Syntax:

```adoscript
{% raw %}
  CC "AdoSript" EDITBOX text:strValue [ title:strValue ] [ oktext:strValue ] 
						[ fontname:strValue ] [ fontheight:intValue ] [ fileeditor ].

#--> RESULT endbutton:strValue text:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`text`|strValue, sets the default text that is contained in the edit box after opening it|
|`title`|strValue, the title of the editbox|
|`oktext`|strValue, sets the name of the OK button|
|`fontname`|strValue, the name of the font|
|`fontheight`|intValue, the size of the font|
|`fileeditor`|modifier, if given, the EditBox will have buttons to save/load text from/to a file.|

# Returns:  

|`endbutton`|strValue, contains the name of the button the user pressed to close the dialog.|
|`text`|strValue, the edited text|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" EDITBOX text:"Default text ..." title:"Enter your text" oktext:"Click!"
IF (endbutton = "ok") {
   CC "AdoScript" INFOBOX (text)
}

{% endraw %}
```
{: .line-numbers}

Starts an EDITBOX and lets the user enter some text. When the user clicks the "Ok" button (labeled "Click!"), the text the user entered is printed in an info box. The edit box

![](/images/EDITBOX.png)

