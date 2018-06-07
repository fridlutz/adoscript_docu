---
layout: commandcall
category: CommandCall
title: "BROWSER"
tags: 1.3 1.5
---

BROWSER will fill a table according to the field informations specified by content and display it within a window with the given title.

# Syntax:

```adoscript
{% raw %}
  CC "AdoScript" BROWSER title:strValue content:strValue 
						[ fieldsep:strValue ] [ linesep:strValue ]
						[ with-handlecolumn ]  [ max-size ] 
						[ adjust-rows ] [ alignment:strValue ]
						[ header:strValue ] [ print-header:strValue ] 
						[show-links] [ modref-format:strValue ]
						[ objref-format:strValue ].

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`title`|strValue|
|`content`|strValue|
|`fieldsep`|strValue, character that defines the limit of a field. If no fieldsep is given, ';' is supposed to define the field limits.|
|`linesep`|strValue, character that defines the end of a table row. If no linesep is given, '\n' is supposed to define the end of a row.|
|`with-handlecolumn`|modifier, specifies the type of the table. If this argument is passed, the table has a first gray column (maybe used as row titles). In this case, the topleft field is always empty.|
|`max-size`|modifier, when passed, the displayed window will totally fill the screen.|
|`adjust-rows`|modifier|
|`alignment`|strValue, defines the alignment of the data columns. The string value has to consist of the letters L for left, C for centered and R for right, one for every data column (the handle column is not taken in account).|
|`header`|strValue, sets the header for saving the content with the header option enabled|
|`print-header`|strValue, sets the print header for printing, using a page layout with a header|
|`show-links`|modifier, if passed, the table is able to display links (interrefs). If a cell value has the LEO interref syntax, then this cell value is interpreted as an interref which can be followed by clicking on it.|
|`modref-format`|strValue, allow to format such an interref value when displayed within the table, for model references.|
|`objref-format`|strValue, allow to format such an interref value when displayed within the table, for object references.|

# Returns:  

|`ecode`|intValue, is either 0 or 1, 0 indicating a successful fill and display. The filling will fail, if the content string is inconsistent,|
i.e. if the number of columns is not the same in each table row or if (besides the column titles) the table contains no rows.

# Remarks:

The information how to interpret the content string is specified by fieldsep and linesep.

Specifying a linesep other than '\n' allows to create a table with cell values that have more lines: \n will then be interpreted as the linebreak within a cell value.

In order to show in the latter case directly the full cell values (i.e. all lines), the argument adjust-rows can be used. If this is given, the heights of the rows are automatically adjusted such that all lines will be displayed.

A linebreak within columnheaders is not supported, '\n' characters there will be converted to blanks!

The expected syntax for an interref cell value is  
&gt; REF mt:strValue m:strValue [c:strValue o:strValue].

As format specifiers %t (for the modeltype), %m (for modelname), %c (for classname), and %o (for objectname) are supported.  
If modref-format is not given, the default value is "%m (%t)".  
If objref-format is not given, the default value is "%o (%c) - %m (%t)".

Both modref-format and objref-format refer to the whole table. So the format for model references resp. object references can be defined only once and is valid for all displayed references in the table!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" BROWSER	title:"My browser window" 
						content:";Column 1;Column 2\t
							Row 1;Value 11\nAdditional line;Value 12\t
							Row 2;Value 21;Value 22\t
							Row 3;Value 31;Value 32" 
						linesep:"\t" 
						adjust-rows with-handlecolumn alignment:"LR" 
						header:"Save\nthis header" print-header:"Print\nthis header"
{% endraw %}
```
{: .line-numbers}
will show the following table

![](/images/BROWSER1.png)

Example 2:

```adoscript
{% raw %}

CC "AdoScript" BROWSER 	show-links 
						objref-format:"%c: %o (of model %m [%t])" 
						modref-format:"Model %m of type %t"
						title:"My browser window"
						content:";Type;Reference\n
							1;Modelreference;REF mt:\"Sample Static Model\" m:\"Sample Static Model 1\"\n
							2;Objectreference;REF mt:\"Sample Static Model\" m:\"Sample Static Model 1\" c:\"T\" o:\"T-3\""
						with-handlecolumn header:"Save\nthis header" print-header:"Print\nthis header"
{% endraw %}
```
{: .line-numbers}
will show the following table

![](/images/BROWSER2.png)

