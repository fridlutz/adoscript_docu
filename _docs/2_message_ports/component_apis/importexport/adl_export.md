---
layout: commandcall
category: CommandCall
title: "ADL_EXPORT"
tags: 1.3 1.5
---

ADL_EXPORT exports models, modelgroups, attributprofiles and attribute profile groups to an ADL file.

# Syntax:  

```adoscript
{% raw %}
ADLExport:	ADLExportByOptions | ADLExportByName | ADLExportById .

ADLExportByOptions: CC "ImportExport" ADL_EXPORT fileName ModelOptions AttrprofOptions [ no-overwrite ] [ verbose ].

ModelOptions: [ modelids:strValue ] [ modelgroupids:strValue ] 
			  [ with-referenced-models ] [ with-models ]
			  [ with-mgroups ] [ mgroups-recursive ] [ with-referenced-attrprofs ] .

AttrprofOptions: [ attrprofids:strValue ] [ apgroupids:strValue ] 
				 [ with-attrprofs ] [ with-apgroups ] [ apgroups-recursive ] .

ADLExportByName: CC "ImportExport" ADL_EXPORT fileName modelname:strValue [ version:strValue ] modeltype:strValue
													   [ with-submodels ] [ with-referenced-models ] [ verbose ].

ADLExportByI: CC "ImportExport" ADL_EXPORT fileName modelids:strValue 
													[ with-submodels ] [ with-referenced-models ] 
													[ verbose ] .

#--> RESULT ecode:intValue  
			errtext:strValue
			modelids:strValue
			attrprofids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|fileName, the name of the ADL file.|

|`modelids`|strValue, the models to be exported. Multiple models can be exported by separating the ids by spaces (" ").|
|`modelgroupids`|strValue, the modelgroups to be exported. Multiple modelgroups can be exported by separating the ids by spaces (" ").|
|`with-referenced-models`|modifier, if given, computes and exports additionally all referenced models from the given models according to the current settings of the Intermodelreferences.|
with-models	- modifier, if given, either export the given models or (if no modelids are given) exports the models that the given modelgroups contain.
|`with-mgroups`|modifier, if given, exports the given modelgroups and their modelreferences.|
|`mgroups-recursive`|modifier, if given, exports the given modelgroups as hierarchy, because with each modelgroup also the whole subtree under the modelgroup is exported.|
|`with-referenced-attrprofs`|modifier, if given, computes and exports additionally all referenced attribute profiles from the given models.|
attrprofids	- strValue, the attribute profiles to be exported. Multiple attribute profiles can be exported by separating the ids by spaces (" ").
|`apgroupids`|strValue, the attribute profile groups to be exported. Multiple attribute profile groups can be exported by separating the ids by spaces (" ").|
|`with-attrprofs`|modifier, if given, either export the given attribute profiles or (if no attrprofids are given) exports the attribute profiles that the given attribute profile groups contain.|
|`with-apgroups`|modifier, if given, exports the given attribute profile groups.|
|`apgroups-recursive`|modifier, if given, exports the given attribute profile groups as hierarchy, because with each attribute profile group also the whole subtree under the attribute profile group is exported.|
|`no-overwrite`|modifier, if given, prevents an already existing adl file to be overwritten.|

# Returns:  

|`ecode`|intValue, specifies whether the export was successful or not. ecode is set to 0 if it was successful, to 1 if not.|
|`errtext`|strValue, gives additional information in case of an error by holding an appropriate error message.|
|`modelids`|strValue, is set to a list of the model ids that have been exported. The modelids are separated by spaces (" ").|
|`attrprofids`|is set to a list of the attribute profile ids that have been exported. The attrprofids are separated by spaces (" ").|

# Remarks:

ADLExportByName and ADLExportById are inheritated from versions &lt; ADOxx 1.2

There the models to be exported can either be specified by modelids or by modelnames. When specifying the models by id, the modelids are passed with the argument modelids. Multiple models can be exported by separating the ids by spaces (" ").

When specifying the model to be exported by name, the name is passed with the argument modelname, the modeltype is passed with the argument modeltype. The version can be passed with the argument version. When specifying the model by name, only one model can be exported to the adl file.

When the argument with-submodels is passed, additionally the models referenced by attribute "Called subprocess" are generated.

When the argument with-referenced-models is passed, the current settings of the Intermodelreferences are used to export all referenced models.

When the argument verbose is passed, a progress bar as well as info- and error boxes are displayed, otherwise the export is performed in silent mode.

# See Also:  

[ADL_IMPORT](adl_import.html "ADL_IMPORT")  
[ADL_EXPORT_APPMODELS](adl_export_appmodels.html "ADL_EXPORT_APPMODELS")  


Example 1:

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_CHILDREN mgroupid:65

SET mg:(VAL token(submgroupids, 0, ""))

CC "ImportExport" ADL_EXPORT "f:\\temp\\file.adl" modelgroupids:(mg) 
								with-models with-modelgroups 
								modelgroups-recursive with-referenced-attrprofs
								
IF (ecode = 0)
{
  SET sInfotext: ("Model-IDs: " + modelids + "\nAttrProf-IDs: " + attrprofids)
  CC "AdoScript" INFOBOX (sInfotext) title:"ADL Export"
}
ELSE
{
  CC "AdoScript" ERRORBOX (errtext) title:"ADL Export"
}
{% endraw %}
```
{: .line-numbers}


