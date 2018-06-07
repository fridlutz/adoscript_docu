---
layout: commandcall
category: CommandCall
title: "SHOW_IMPORT_START_DLG"
tags: 1.3 1.5
---

SHOW_IMPORT_START_DLG shows a dialog for importing models and attribute profiles. The dialog can be used for any import format (e.g. XML) which is interpreted by an AdoScript program.

# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" SHOW_IMPORT_START_DLG	[ title:strValue ]
										[ filedescription:strValue ] 
										[ fileextension:strValue ]
										[ otherlib-opt-visible:boolValue ]
										[ existing-models-vis-items:strValue ]
										[ auto-rename-models-opt-visible:boolValue ]
										[ update-interrefs-opt-visible:boolValue ]
										[ find-by-id-opt-visible:boolValue ]
										[ delete-untouched-recrows-opt-visible:boolValue ]
										[ existing-attrprofs-vis-items:strValue ]
										[ auto-rename-attrprofs-opt-visible:boolValue ]
										[ update-attrprofrefs-opt-visible:boolValue ]
										[ filename:strValue ] 
										[ otherlib:boolValue ]
										[ existing-models:ExistingTreatment ]
										[ auto-rename-models:boolValue ]
										[ models-prefix:strValue ] 
										[ models-suffix:strValue ]
										[ update-interrefs:boolValue ]
										[ adopt-version-into-name:boolValue ]
										[ find-by-id:boolValue ]
										[ delete-recordrows:boolValue ]
										[ delete-unchanged-objects:boolValue ]
										[ delete-unchanged-connectors:boolValue ]
										[ delete-untouched-recrows:boolValue ]
										[ existing-attrprofs:ExistingTreatment ]
										[ auto-rename-attrprofs:boolValue ]
										[ attrprofs-prefix:strValue ]
										[ attrprofs-suffix:strValue ]
										[ update-attrprofrefs:boolValue ]
										[ delete-attrprof-recordrows:boolValue ]
										[ with-protocol:boolValue ]
										[ protocol-filename:strValue ] 
										[ mode: "adl" | "xml" ]

#--> RESULT endbutton: "ok" | "cancel" 
			filename:strValue otherlib:boolValue
			existing-models:ExistingTreatment
			auto-rename-models:boolValue
			models-prefix:strValue models-suffix:strValue
			update-interrefs:boolValue
			adopt-version-into-name:boolValue
			find-by-id:boolValue
			delete-recordrows:boolValue
			delete-unchanged-objects:boolValue
			delete-unchanged-connectors:boolValue
			delete-untouched-recrows:boolValue
			existing-attrprofs:ExistingTreatment
			auto-rename-attrprofs:boolValue
			attrprofs-prefix:strValue 
			attrprofs-suffix:strValue
			update-attrprofrefs:boolValue
			delete-attrprof-recordrows:boolValue
			with-protocol:boolValue 
			protocol-filename:strValue

ExistingTreatment =	"overwrite" | "paste" | "rename" | "ignore" | "increase-version" .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`title`|strValue, dialog title; default is "ADL import options"|
|`filedescription`|strValue, file type information; default is "ADL files"|
|`fileextension`|strValue, filter for the file dialog; default: "**.adl".|
|`otherlib-opt-visible`|boolValue, visibility of the checkbox "Import objects from different library".|
|`existing-models-vis-items`|strValue, if this value is not specified, all items of the dropdown listbox "Strategy on same model name" are visible. Otherwise, only those items are visible, whose corresponding tokens are contained in the string value. The tokens are "overwrite", "paste", "rename", "ignore" and "increase-version". The token separator is " " (blank). E.g. "overwrite paste" is a possible value.|
|`auto-rename-models-opt-visible`|boolValue, visibility of the checkbox "Rename all imported models automatically" and its prefix and suffix edit fields.|
|`update-interrefs-opt-visible`|boolValue, visibility of the checkbox "Update model references".|
|`find-by-id-opt-visible`|boolValue, visibility of the checkbox "Find existing elements by IDs". Default is 0 (hidden).|
|`delete-untouched-recrows-opt-visible`|boolValue|
|`existing-attrprofs-vis-items`|strValue, if this value is not specified, all items of the dropdown listbox "Strategy on same attribute profile name" are visible. Otherwise, only those items are visible, whose corresponding tokens are contained in the string value. The tokens are "overwrite", "paste", "rename", "ignore" and "increase-version". The token separator is " " (blank). E.g. "overwrite paste" is a possible value.|
|`auto-rename-attrprofs-opt-visible`|boolValue, visibility of the checkbox "Rename all imported attribute profiles automatically" and its prefix and suffix edit fields.|
|`update-attrprofrefs-opt-visible`|boolValue, visibility of the checkbox "Update attribute profile references".|
|`filename`|strValue, name of the import file.|
|`otherlib`|boolValue, option "Import objects from different library".|
|`existing-models`|How shall existing models be treated? Possible values are "overwrite", "paste", "rename", "ignore" and "increase-version" .|
|`auto-rename-models`|boolValue, model option "Rename all models automatically".|
|`models-prefix`|strValue, prefix for automatic renaming of all imported models.|
|`models-suffix`|strValue, suffix for automatic renaming of all imported models.|
|`update-interrefs`|boolValue, model option "Update model references".|
|`adopt-version-into-name`|boolValue, model option "Adopt version number into model name".|
|`find-by-id`|boolValue, model option "Find existing elements by IDs".|
|`delete-recordrows`|boolValue, model option "Replace existing record rows". Replacing (1) means deleting original record rows and adding imported record rows. Not replacing (0) means just appending imported record rows. If existing-models is not "paste", the value is always 0.|
|`delete-unchanged-objects`|boolValue, model option "Delete not actualized instances". If existing-models is not "paste", the value is always 0.|
|`delete-unchanged-connectors`|boolValue, model option "Delete not actualized relations". If existing-models is not "paste", the value is always 0.|
|`delete-untouched-recrows`|boolValue|
|`existing-attrprofs`|how shall existing attribute profiles be treated? Possible values are "overwrite", ""paste", "rename", "ignore" and "increase-version" .|
|`auto-rename-attrprofs`|boolValue, attribute profile option "Rename all imported attribute profiles automatically".|
|`attrprofs-prefix`|strValue, prefix for automatic renaming of all imported attribute profiles.|
|`attrprofs-suffix`|strValue, suffix for automatic renaming of all imported attribute profiles.|
|`update-attrprofrefs`|boolValue, attribute profile option "Update attribute profile references".|
|`delete-attrprof-recordrows`|boolValue, option "Replace existion record rows". Replacing (1) means deleting original record rows and adding imported record rows. Not replacing (0) means just appending imported record rows. If existing-attrprofs is not "paste", the value is always 0.|
|`with-protocol`|boolValue, option "Generate protocol".|
|`protocol-filename`|strValue, name of the protocol file. Is an empty string if no protocoll shall be written.|
|`mode`| "adl" | "xml", tells the dialog if it is used for ADL or XML import; Default = ADL|

# Returns:  

|`endbutton`| "ok" | "cancel" , if "cancel", all other result values are not set!|
|`filename`|strValue, name of the import file.|
|`otherlib`|boolValue, option "Import objects from different library".|
|`existing-models`|How shall existing models be treated? Possible values are "overwrite", "paste", "rename", "ignore" and "increase-version" .|
|`auto-rename-models`|boolValue, model option "Rename all models automatically".|
|`models-prefix`|strValue, prefix for automatic renaming of all imported models.|
|`models-suffix`|strValue, suffix for automatic renaming of all imported models.|
|`update-interrefs`|boolValue, model option "Update model references".|
|`adopt-version-into-name`|boolValue, model option "Adopt version number into model name".|
|`find-by-id`|boolValue, model option "Find existing elements by IDs".|
|`delete-recordrows`|boolValue, model option "Replace existing record rows". Replacing (1) means deleting original record rows and adding imported record rows. Not replacing (0) means just appending imported record rows. If existing-models is not "paste", the value is always 0.|
|`delete-unchanged-objects`|boolValue, model option "Delete not actualized instances". If existing-models is not "paste", the value is always 0.|
|`delete-unchanged-connectors`|boolValue, model option "Delete not actualized relations". If existing-models is not "paste", the value is always 0.|
|`delete-untouched-recrows`|boolValue|
|`existing-attrprofs`|how shall existing attribute profiles be treated? Possible values are "overwrite", ""paste", "rename", "ignore" and "increase-version" .|
|`auto-rename-attrprofs`|boolValue, attribute profile option "Rename all imported attribute profiles automatically".|
|`attrprofs-prefix`|strValue, prefix for automatic renaming of all imported attribute profiles.|
|`attrprofs-suffix`|strValue, suffix for automatic renaming of all imported attribute profiles.|
|`update-attrprofrefs`|boolValue, attribute profile option "Update attribute profile references".|
|`delete-attrprof-recordrows`|boolValue, option "Replace existion record rows". Replacing (1) means deleting original record rows and adding imported record rows. Not replacing (0) means just appending imported record rows. If existing-attrprofs is not "paste", the value is always 0.|
|`with-protocol`|boolValue, option "Generate protocol".|
|`protocol-filename`|strValue, name of the protocol file. Is an empty string if no protocoll shall be written.|

# Remarks:

Some of the result parameter names contain minus signs ('-'). If you want to use a variable name containing one or more minus signs within an expression, you have to prevent the LEO compiler from interpreting them as minus operator by prefixing the variable name with a quotation mark ('?') or by the expression valofvar (). So, within an expression, instead of protocol-filename you have to write ?protocol-filename or valofvar ("protocol-filename").

# See Also:  

[SHOW_IMPORT_SELECT_DLG](show_import_select_dlg.html "SHOW_IMPORT_SELECT_DLG")  
[SHOW_EXPORT_DLG](show_export_dlg.html "SHOW_EXPORT_DLG")  


Example 1:

```adoscript
{% raw %}

CC "ImportExport" SHOW_IMPORT_START_DLG 
  title:("XML-Import - Einstellungen")
  filedescription:("XML-Dateien")
  fileextension:"**.xml"
  filename:("C:\\")
  otherlib-opt-visible:(0)
  existing-models-vis-items:"overwrite paste ignore"
  auto-rename-models-opt-visible:(0)
  update-interrefs-opt-visible:(0)
  find-by-id-opt-visible:(1)
  delete-untouched-recrows-opt-visible:(1)
  existing-attrprofs-vis-items:"overwrite ignore"
  auto-rename-attrprofs-opt-visible:(0)
  update-attrprofrefs-opt-visible:(0)
  with-protocol:(1)
  protocol-filename:("C:\\log.txt")

SETL str_protocol_filename:(?protocol-filename)

# or:
# SETL str_protocol_filename:(valofvar("protocol-filename"))

{% endraw %}
```
{: .line-numbers}

