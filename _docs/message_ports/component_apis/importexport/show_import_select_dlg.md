---
layout: commandcall
category: CommandCall
title: "SHOW_IMPORT_SELECT_DLG"
tags: 1.3 1.5
---

SHOW_IMPORT_SELECT_DLG shows a dialog where models, modelgroups, attribute profiles and attribute profile groups can be selected for a custom import.


# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" SHOW_IMPORT_SELECT_DLG 	[ title:strValue ]
											[ with-models:boolValue ]
											[ with-mgroups:boolValue ]
											[ mgroups:MGroups ]
											[ import-mgroups:boolValue ]
											[ with-attrprofs:boolValue ]
											[ with-apgroups:boolValue ]
											[ apgroups:APGroups ]
											[ import-apgroups:boolValue ]
											[ mode:"adl" | "xml" ] 

#--> RESULT endbutton:"ok" | "cancel"
			sel-models:SelModels 
			import-mgroups:boolValue mgroupid:id
			sel-attrprofs:SelAttrProfs 
			import-apgroups:boolValue apgroupid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

title - strValue, dialog title; default: "ADL import - selection"
|`with-models`|boolValue, set this value to 0 if the import file does not contain models; default: 1|
|`with-mgroups`|boolValue, set this value to 0 if the import file does not contain model groups; default: 1.|
|`mgroups`|MGroups, LEO text which specifies the models and model groups of the import file; see syntax below.|
|`import-mgroups`|boolValue, state of the checkbox "Include model groups".|
|`with-attrprofs`|boolValue, set this value to 0 if the import file does not contain attribute profiles; default: 1.|
|`with-apgroups`|boolValue, set this value to 0 if the import file does not contain attribute profile groups; default: 1.|
|`apgroups`|APGroups, LEO text which specifies the attribute profiles and attribute profile groups of the import file; see syntax below.|
|`import-apgroups`|boolValue, state of the checkbox "Include attribute profile groups".|
|`mode`|"adl" | "xml" , tells the dialog if it is used for ADL or XML import; default: ADL.|

# Returns:  

|`endbutton`|"ok" | "cancel"; if "cancel", all other result values are not set!|
|`sel-models`|SelModels, LEO text which specifies the selected models. See syntax below.|
|`import-mgroups`|boolValue, state of the checkbox "Include model groups".|
|`mgroupid`|id, ID of the selected target model group, or -1 if none has been selected.|
|`sel-attrprofs`|SelAttrProfs, LEO text which specifies the selected attribute profiles. See syntax below.|
|`import-apgroups`|boolValue, state of the checkbox "Include attribute profile groups".|
|`apgroupid`|id, ID of the selected attribute profile group, or -1 if none has been selected|

# Remarks:  
MGroups is a string value containing LEO code with the following syntax  
```adoscript
{% raw %}
MGroups	: { MGroup | Model }
MGroup 	: MGROUP name:strValue
Model 	: MODEL name:strValue version:strValue type:strValue
{% endraw %}
```
{: .line-numbers}

APGroups is a string value containing LEO code with the following syntax  
```adoscript
{% raw %}
APGroups: { APGroup | AttrProf }
APGroup	: APGROUP name:strValue
AttrProf: ATTRPROF name:strValue version:strValue apclassname:strValue
{% endraw %}
```
{: .line-numbers}

SelModels is a string value containing LEO code with the following syntax  
```adoscript
{% raw %}
SelModels	: { Model }
Model 		: MODEL path:strValue name:strValue version:strValue type:strValue
{% endraw %}
```
{: .line-numbers}

SelAttrProfs is a string value containing LEO code with the following syntax  
```adoscript
{% raw %}
SelAttrProfs: { AttrProf }
AttrProf	: ATTRPROF path:strValue name:strValue version:strValue apclassname:strValue
{% endraw %}
```
{: .line-numbers}

# See Also:  

[SHOW_IMPORT_SELECT_DLG](show_import_select_dlg.html "SHOW_IMPORT_SELECT_DLG")  
[SHOW_EXPORT_DLG](show_export_dlg.html "SHOW_EXPORT_DLG")  


Example 1:

```adoscript
{% raw %}
SET m1:"name:\"vier\" version:\"1.0\" type:\"Gesch�ftsproze�modell\""
SET m2:"name:\"vier\" version:\"1.0\" type:\"Gesch�ftsproze�modell\""
SET m3:"name:\"quark\" version:\"1.0\" type:\"Gesch�ftsproze�modell\""

SET mgroups:""
SET mgroups:(mgroups + "MGROUP name:\"eins\" {\n")
SET mgroups:(mgroups + "  MODEL " + m1 + "\n")
SET mgroups:(mgroups + "  MGROUP name:\"eins a\" {\n")
SET mgroups:(mgroups + "    MODEL " + m3 + "\n")
SET mgroups:(mgroups + "  }\n")
SET mgroups:(mgroups + "}\n")
SET mgroups:(mgroups + "MGROUP name:\"zwei\"\n")
SET mgroups:(mgroups + "MGROUP name:\"drei\"\n")
SET mgroups:(mgroups + "MODEL " + m2 + "\n")

SET ap1:"name:\"drei\" version:\"1.0\" apclassname:\"Test\""
SET ap2:"name:\"vier\" version:\"1.0\" apclassname:\"Test\""

SET apgroups:""
SET apgroups:(apgroups + "APGROUP name:\"eins\" {\n")
SET apgroups:(apgroups + "  APGROUP name:\"zwei\" {\n")
SET apgroups:(apgroups + "    ATTRPROF " + ap1 + "\n")
SET apgroups:(apgroups + "    ATTRPROF " + ap2 + "\n")
SET apgroups:(apgroups + "  }\n")
SET apgroups:(apgroups + "}\n")

CC "ImportExport" debug SHOW_IMPORT_SELECT_DLG
    title:"XML-Import - Auswahl"
    with-models:1 with-mgroups:1 with-attrprofs:1 with-apgroups:1
    mgroups:(mgroups) apgroups:(apgroups)
{% endraw %}
```
{: .line-numbers}

