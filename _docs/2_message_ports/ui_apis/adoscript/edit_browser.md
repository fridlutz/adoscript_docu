---
layout: commandcall
category: CommandCall
title: "EDIT_BROWSER"
tags: 1.3 1.5
---

EDIT_BROWSER will fill a table according to the field informations specified by content and display it within a window (with title title).

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" EDIT_BROWSER	[ title:strValue ] [ content:strValue ] 
							[ fieldsep:strValue ] [ header:strValue ] 
							[ print-header:strValue ] [ no-special-buttons ] 
							[ with-handlecolumn ]  [ max-size ] 
							[ alignment:strValue ].

# --> RESULT ecode:intValue text:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`title`|strValue|
|`content`|strValue|
|`fieldsep`|strValue, contains the information how to interpret the content string. This character defines the limit of a field within the table, while '\n' is the character that defines the end of a table row. If no fieldsep is given, ';' is supposed to define the field limits. The filling will fail, if the content string is inconsistent,i.e. if the number of columns is not the same in each table row or if (besides the column titles) the table contains no rows.|
|`header`|strValue|
|`print-header`|strValue|
|`no-special-buttons`|modifier, when given, the save, print and search buttons are not displayed.|
|`with-handlecolumn`|modifier, if passed, the table has a first gray column (maybe used as row titles). In this case, the topleft field is always empty.|
|`max-size`|modifier, when passed, the window is maximized.|
|`alignment`|strValue, defines the alignment of the data columns. The string value has to consist of the letters L for left, C for centered and R for right, one for every data column (the handle column is not taken in account). Note that using C or R will not work correctly for cells with multiline content.|

# Returns:  

|`ecode`|intValue, is either 0 or 1, 0 indicating a successful fill and display.|
|`text`|strValue, contains the browser contents. Only the editable fields are taken in account.|

# Remarks:

Passing the optional header and/or print-header strings sets the header for saving the content with the header option enabled and the print header for printing, using a page layout with a header, respectively.

Once the browser has been displayed the field contents can be edited by the user. After the close-button is pushed the browser window is closed and its contents are returned to the AdoScript where EDIT_BROWSER has been called.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" EDIT_BROWSER title:"My editable browser window" 
							content:";Column 1;Column 2; Column 3\n
								Row 1;Value 11;Value 12;Value 13\n
								Row 2;Value 21;Value 22;Value 23\n
								Row 3;Value 31;Value 32;Value 33" 
							oktext:"Erledigt" with-handlecolumn alignment:"LCR"
							header:"Save\nthis header" print-header:"Print\nthis header" 
IF (ecode = 0) {
   CC "AdoScript" INFOBOX (text)
}

{% endraw %}
```
{: .line-numbers}

displays the following table

![](/images/EDIT_BROWSER.png)

