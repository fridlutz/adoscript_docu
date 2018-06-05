---
layout: commandcall
category: CommandCall
title: "FILE_DIALOG"
tags: 1.3 1.5
---

FILE_DIALOG shows a file selection dialog.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" FILE_DIALOG	Mode 
							[ path:strValue ] [ filename: strValue]
							[ filter1:strValue type1:strValue ]
							[ filter2:strValue type2:strValue ]
							...
							[ filtern:strValue typen:strValue ]
							[ default-ext:strValue ]

Mode :		Open | SaveAs .

Open :		open [ multi-sel: boolValue ] .

SaveAs :	saveas .

# --> RESULT endbutton:strValue path:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`open`|modifier, in open mode, the file dialog is displayed as a "Open file" dialog. By default, you can select exactly one file.|
|`multi-sel`|boolValue, when true, more than one file can be selected.|
|`saveas`|modifier, in saveas mode, the dialog is displayed as a "Save file" dialog.|
|`path`|strValue, selects the starting directory in which the file dialog should be opened|
|`filename`| strValue, if given, it is preset in the field for the filename.|
|`filteri`|strValue, description for filetypes|
|`typei`|strValue, extension of file types|
|`default-ext`|strValue, the default file extension|


# Returns:  

|`endbutton`|strValue, contains the name of the button the user pressed.|
|`path`|strValue, contains the absolute path to the file the user selected in the dialog.|

# Remarks:

Relative paths relate to the current working directory (CWD).

By default only one file can be selected. When multi-sel is set, multi-selection is allowed.

In open mode, when multi-sel is set, path is an array of such file name strings.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG open 
   filter1:"XML Files" type1:"**.xml" default-ext:"xml"
   filter2:"HTML Files" type2:"**.htm" 
CC "AdoScript" INFOBOX ("You selected " + path)

{% endraw %}
```
{: .line-numbers}

Starts a file dialog with two filters, one for html and one for xml files.  
