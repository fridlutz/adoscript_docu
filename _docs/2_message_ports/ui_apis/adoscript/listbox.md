---
layout: commandcall
category: CommandCall
title: "LISTBOX"
tags: 1.3 1.5
---

LISTBOX opens a box where the user can select values of a list of values. In a LISTBOX, the user can only select one value out of a list, in a MLISTBOX the user can select multiple values of the list.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" LISTBOX entries:strValue [ toksep:strValue ] 
						 [ selection:strValue ] [ title:strValue ] 
						 [ boxtext:strValue ] [ oktext:strValue ] 
						 [ w:intValue h:intValue ] [ extra:{ Extra } ].

Extra :		{ CheckBox }

CheckBox :	CHECKBOX cbText [ checked:intValue ] result-var:varName

cbText:	strValue

 # --> RESULT endbutton:strValue selection:strValue [ extraValues ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`entries`|strValue, the possible values for selection. The values have to be separated by a character specified with toksep.|
|`toksep`|strValue|
|`selection`|strValue, sets preselected values|
|`title`|strValue, the window title is set with title.|
|`boxtext`|strValue, the label of the listbox|
|`oktext`|strValue , the label of the "Ok" button|
|`w`|intValu, the width of the dialog|
|`h`|intValue, the height of the dialog|
|`extra`|strValue, inserts additional checkboxes in the mlistbox. For each check box, the keyword CHECKBOX followed by the label of the checkbox has to be specified. Set the argument checked to 1 if the checkbox should be checked when the dialog is started, set it to 0 if not. For each checkbox, the name of a result variable is specified. After closing the dialog, the result variables are set to 1 if the checkbox has been checked, to 0 if not.|

# Returns:  

|`endbutton`|strValue, contains the name of the button the user pressed to close the dialog.|
|`selection`|strValue, contains a list of the selected values separated by the character specified with toksep.|
extraValues -

# Remarks:



# See Also:  

[MLISTBOX](mlistbox.html "MLISTBOX")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" LISTBOX 	entries:"First Entry;Second Entry;Third;Fourth;Fifth Entry" 
						toksep:";" 
						title:"Example!" 
						oktext:"Click me!" 
						boxtext:"Choose your entry:" 
						selection:"Second Entry"
IF (endbutton = "ok") {
   CC "AdoScript" INFOBOX (selection)
}

{% endraw %}
```
{: .line-numbers}

Starts an LISTBOX with the entries "First Entry", "Second Entry", "Third", "Fourth" and "Fifth Entry". As entries are separated by the character ";", toksep:";" defines this character as the separator. The second entry is preselected.

After the user selected some other entry and clicks the "Ok" button, the return value is displayed in an info box.  

Example 2:

```adoscript
{% raw %}

CC "AdoScript" LISTBOX 	entries:"First Entry;Second Entry;Third;Fourth;Fifth Entry" toksep:";" 
						title:"Example!" 
						oktext:"Click me!" 
						boxtext:"Choose your entry:" 
						selection:"Third" 
						extra:{ CHECKBOX "Option 1" checked:1 result-var:option1 
								CHECKBOX "Option 2" result-var:option2}
IF (endbutton = "ok") {
   CC "AdoScript" INFOBOX (selection + "\nOption1="+STR option1+"\nOption2="+STR option2)
}

{% endraw %}
```
{: .line-numbers}
