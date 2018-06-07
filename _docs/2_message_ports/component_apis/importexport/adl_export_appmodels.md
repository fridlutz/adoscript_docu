---
layout: commandcall
category: CommandCall
title: "ADL_EXPORT_APPMODELS"
tags: 1.3 1.5
---

ADL_EXPORT_APPMODELS exports applicationmodels and its model parts to an adl file.

# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" ADL_EXPORT_APPMODELS  fileName  appmodelids:strValue 
										[ with-referencedmodels ] 
										[ export-threads ] [ no-overwrite ] [ verbose ]

#--> RESULT ecode:intValue  
			errtext:strValue
			modelids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|fileName, a string containing the target file name and path.|
|`appmodelids`|strValue, the application models to be exported. Multiple application models can be exported by separating the ids by spaces (" ").|
|`with-referencedmodels`|modifier, if given, computes and exports additionally all referenced models from the application models parts according to the current settings of the Intermodelreferences.|
|`export-threads`|modifier, if given, supposes that the modelids refer to application models that are defined on threads and exports the application model definition accordingly. If not given, supposes that the modelids refer to application models that are defined on versions.|
|`no-overwrite`|modifier, if given, prevents an already existing adl file to be overwritten.|
|`verbose`|modifier, if given, a progress bar as well as info- and error boxes are displayed, otherwise the export is performed in silent mode.|

# Returns:  

|`ecode `|intValue, specifies whether the export was successful or not. ecode is set to 0 if it was successful, to 1 if not.|
|`errtext`|strValue, gives additional information in case of an error by holding an appropriate error message.|
|`modelids`|strValue, is set to a list of the model ids that have been exported. This includes both the models and the application models. The modelids are separated by spaces (" ").|

# Remarks:

The adl file is specified with fileName.

# See Also:  

[ADL_EXPORT](adl_export.html "ADL_EXPORT")  
[ADL_IMPORT_APPMODELS](adl_import_appmodels.html "ADL_IMPORT_APPMODELS")  


Example 1:

```adoscript
{% raw %}

CC "Core" GET_ALL_APPMODEL_IDS 

CC "ImportExport" ADL_EXPORT_APPMODELS "f:\\temp\\file.adl" appmodelids:(appmodelids) with-referenced-models verbose

IF (ecode = 0)
{
  SET sInfotext: ("Model-IDs: " + modelids)
  CC "AdoScript" INFOBOX (sInfotext) title:"ADL Application Model Export"
}
ELSE
{
  CC "AdoScript" ERRORBOX (errtext) title:"ADL Application Model Export"
}

{% endraw %}
```
{: .line-numbers}

Exporting all Application models in verbose mode

