---
layout: commandcall
category: CommandCall
title: "EDITFIELD"
tags: 1.3 1.5
---

EDITFIELD opens a simple edit box with a single line text field.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" EDITFIELD caption:strValue [ title:strValue ] [ text:strValue ].

#--> RESULT ecode:0|1  [ text:strValue ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`caption`|strValue, sets the caption of the text field.|
|`title`|strValue, sets the title of the edit box.|
|`text`|strValue, sets the default text.|

# Returns:  

|`ecode`|0|1 , is set to 0 if the user hits the OK button, otherwise to 1.|
|`text`|strValue, contains the entered text if ecode was 0. It is not present if ecode is 1.|

# Remarks:

Key shortcuts (accelerators) can be set by using '~'. (See example below.)

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" EDITFIELD title:"Enter web address" caption:"Web ~address:" text:"http://www.adoxx.org"
IF (ecode = 0) {
   CC "AdoScript" INFOBOX (text)
}

{% endraw %}
```
{: .line-numbers}

Opens the following window:

![](/images/EDITFIELD.png)

