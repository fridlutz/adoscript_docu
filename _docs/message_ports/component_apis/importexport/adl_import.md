---
layout: commandcall
category: CommandCall
title: "ADL_IMPORT"
tags: 1.3 1.5
---

ADL_IMPORT starts the ADL import.

# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" ADL_IMPORT fileName [ otherlib ]
							ModelSettings AttrProfSettings
							[ protfile:fileName ]
							[ import-versioned-file ] [ appmodels ]
							[ silent ] [ abort-with-mixed-libs ] .

ModelSettings :	[ existing-models:ExistingTreatment ]
				ModelSuboptions
				[ with-mgroups ] [ target-mgroupid:id ]

ModelSuboptions : [ update-interrefs ]
				[ delete-recordrows ]
				[ delete-unchanged-objects ]
				[ delete-unchanged-connectors ]
				[ adopt-version-into-name ]
				[ models-prefix:strValue ] [ models-suffix:strValue ]

AttrProfSettings : [ existing-attrprofs:ExistingTreatment ]
				AttrProfSuboptions
				[ with-apgroups ] [ target-apgroupid:id ]

AttrProfSuboptions : [ update-attrprofrefs ]
					[ delete-attrprof-recordrows ]
					[ attrprofs-prefix:strValue ] [ attrprofs-suffix:strValue ]

ExistingTreatment :	overwrite | paste | rename | ignore | increase-version

#--> RESULT ecode:intValue 
			errtext:strValue 
			modelids:idCont 
			attrprofids:idCont .
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`existing-models`|if given, specifies the treatment for models that already exist in the database. Five options are possible: overwrite, paste, rename, ignore, increase-version|
|`with-mgroups`|modifier, if given, specifies that also the modelgroup hierarchy of the ADL file should be imported.|
|`target-mgroupid`|modifier, if given, specifies the target modelgroup for the imported models resp. modelgroups.|
|`update-interrefs`|modifier, if given, specifies that the model interreferences within the imported model set should be updated if the names of models were changed during import.|
|`update-interreferences`|modifier, if given, specifies that the model interreferences within the imported model set should be updated if the names of models were changed during import.|
|`delete-recordrows`|modifier, if given, specifies that within the existing-models option 'paste' existing record rows are deleted before new rows from the ADL file are inserted in an object. In all other existing-models options the argument is ignored.|
|`delete-unchanged-objects`|modifier, if given, specifies that within the existing-models option 'paste' already existing objects that are not changed by the import are deleted from the model. In all other existing-models options the argument is ignored.|
|`delete-unchanged-connectors`|modifier, if given, specifies that within the existing-models option 'paste' already existing connectors that are not changed by the import are deleted from the model. In all other existing-models options the argument is ignored.|
|`adopt-version-into-name`|modifier, if given, specifies that the new name of the model is generated from the old one + the version number|
|`models-prefix`|strValue, with this option a string value can be passed for renaming all imported models using this prefix.|
|`models-suffix`|strValue, with this option a string value can be passed for renaming all imported models using this suffix.|
|`existing-attrprofs`|modifier, if given, specifies the treatment for attribute profiles that already exist in the database. Five options are possible: overwrite, paste, rename, ignore, increase-version.|
|`with-apgroups`|modifier, if given, specifies that also the attribute profile group hierarchy of the ADL file should be imported|
|`target-apgroupid`|modifier, if given, specifies the target attribute profile group for the imported attribute profiles resp. attribute profile groups|
|`update-attrprofrefs`|modifier, if given, specifies that the attributeprofile references within the imported model set should be updated if the names of attribute profiles were changed during import.|
|`update-attrprofs-references`|modifier, if given, specifies that the attributeprofile references within the imported model set should be updated if the names of attribute profiles were changed during import.|
|`delete-attrprof-recordrows`|modifier, if given, specifies that within the existing-attrprofs option 'paste' existing record rows are deleted before new rows from the ADL file are inserted in an attribute profile. In all other existing-attrprofs options this argument is ignored.|
|`attrprofs-prefix`|strValue, with this option a string value can be passed for renaming all imported attribute profiles using this prefix.|
|`attrprofs-suffix`|strValue, with this option a string value can be passed for renaming all imported attribute profiles using this suffix.|
|`import-versioned-file`|modifier, if given, allows to import ADL files from versioned libraries and risk inconsistent data (like broken references) in special cases.|
|`appmodels`|modifier, if given, performs an application model import. Note: Because the application model import does not allow any suboptions, better use ADL_IMPORT_APPMODELS instead!|
|`protfile`|modifier, if given, specifies a filename for a protocol file with log messages of the ADL import.|
|`otherlib`|modifier, if given, sets the option "import objects from other library".|
|`silent`|modifier, if given, imports in silent mode, i.e. no user interaction is necessary. A valid target-modelgroupid must be given. A target-apgroupid must be given unless with-attrprofgroups is used.|
|`abort-with-mixed-libs`|modifier, if given, importing an ADL file containing more than one libraries is aborted.|

# Returns:  

|`ecode`|specifies whether the adl file was imported successfully or not. ecode is set to 0 if the import worked, to 1 if not.|
|`errtext`|contains an error text that could be displayed (in the case ecode = 1).|
|`modelids`|is set to a list of the model ids that have been imported. The modelids are separated by spaces (" ").|
|`attrprofids`|is set to a list of the attribute profile ids that have been imported. The attrprofids are separated by spaces (" ").|

# Remarks:


If the argument silent is given, and the ADL file contains models or modelgroups also a target-modelgroupid has to be specified. If the ADL file contains attributeprofiles, additionally a target-attrprofgroupid has to be specified. Otherwise the import will yield an error.

# See Also:  

[ADL_EXPORT](adl_export.html "ADL_EXPORT")  
[ADL_IMPORT_APPMODELS](adl_import_appmodels.html "ADL_IMPORT_APPMODELS")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG open filter1:"ADL Filesss" type1:"**.adl"
IF (endbutton != "ok") {
   EXIT
}
CC "AdoScript" GET_TEMP_FILENAME

CC "ImportExport" ADL_IMPORT (path) otherlib
        existing-models:overwrite protfile:(filename)
        models-prefix:">" models-suffix:"<"
        attrprofs-prefix:">" attrprofs-suffix:"<"
        update-interrefs update-attrprofrefs
IF (ecode = 0) {
   CC "AdoScript" FREAD file:(filename)
   CC "AdoScript" VIEWBOX text:(text)
}

{% endraw %}
```
{: .line-numbers}

At first, the file dialog is shown and the user selects an ADL file. At next, a temporary filename is retrieved. After that, the selected file is imported with mode "overwrite" and with full renaming plus reference updating. A protocol is written to the temporary file. If the import was successful, the content of the protocol file is displayed.

