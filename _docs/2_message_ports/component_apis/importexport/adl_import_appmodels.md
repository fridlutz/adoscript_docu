---
layout: commandcall
category: CommandCall
title: "ADL_IMPORT_APPMODELS"
tags: 1.3 1.5
---

ADL_IMPORT_APPMODELS starts the ADL import.  
# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" ADL_IMPORT_APPMODELS fileName [ target-mgroupid:intValue ]�[ protfile:strValue ] 
											    [ otherlib ] [ import-versioned-file ] [ silent ]

#--> RESULT ecode:intValue 
			errtext:strValue 
			modelids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|fileName, a string containing the file name and path to be imported.|
|`target-mgroupid`|intValue, if given, specifies the targetmodelgroup for the imported models.|
|`protfile`|strValue, if given, specifies a filename for a protocol file with log messages of the ADL import.|
|`otherlib`|modifier, if given, sets the option "import objects from other library".|
|`import-versioned-file`|modifier, if given, allows to import ADL files from versioned libraries and risk inconsistent data (like broken references) in special cases .|
|`silent`|modifier, if given, imports in a silent mode, i.e. no user interaction is necessary.|

# Returns:  

|`ecode`|intValue, specifies whether the adl file was imported successfully or not. ecode is set to 0 if the import worked, to 1 if not.|
|`errtext`|strValue, contains an error text that could be displayed (in the case ecode = 1).|
|`modelids`|strValue, is set to a list of the model ids that have been imported. This includes the applicationmodels as well. The modelids are separated by spaces (" ").|


# Remarks:

The file that should be imported is specified with fileName.

If the argument silent is given, also a target-modelgroupid has to be specified. Otherwise the import will yield an error.

# See Also:  

[ADL_EXPORT_APPMODELS](adl_export_appmodels.html "ADL_EXPORT_APPMODELS")  
[ADL_IMPORT](adl_import.html "ADL_IMPORT")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG open filter1:"ADL Filesss" type1:"**.adl"
IF (endbutton != "ok")
{
   EXIT
}
CC "AdoScript" GET_TEMP_FILENAME

CC "ImportExport" ADL_IMPORT_APPMODELS (path) protfile:(filename)
IF (ecode = 0)
{
   CC "AdoScript" FREAD file:(filename)
   CC "AdoScript" VIEWBOX text:(text)
}

{% endraw %}
```
{: .line-numbers}

Importing an ADL file

First the file dialog is opened and the user selects an adl file. Next a temporary filename is retrieved. Then the selected file is imported. A protocol is written to the temporary file. If the import was successful, the content of the protocol file is displayed.

