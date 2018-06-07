---
layout: commandcall
category: CommandCall
title: "EXEC_EXPORTDIALOG"
tags: 1.3 1.5
---

EXEC_EXPORTDIALOG starts the export dialog for documentation export. Calling EXEC_EXPORTDIALOG only starts the dialog, no documentation will be generated. Use EXEC_MENUENTRY or DOCU_EXPORT to generate documentation.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" EXEC_EXPORTDIALOG	[ dialogTitle ] [ multi-select: 1|0 ] 
										[ model-groups-selectable: 1|0 ]
										[ filedescription:strValue ] [ fileextension:strValue ]
										[ allowedmodeltypes:strValue ]
										[ sortmode:SortMode ]
										[ no-submodels ] [ submodels: 1|0 ]
										[ selmodelids:strValue ]
										[ needsemptydir: 1|0 ] .

SortMode :	"Breadth-First Search" | "Depth-First Search" | "Lexical Ordering" .

#--> RESULT ecode:intValue 
			filename:strValue
			modelids:strValue 
			selmodelids:strValue 
			refmodelids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|dialogTitle, is, surprisingly, the title for the dialog.|
|`multi-select`| 1|0, allows or not the selection of multiple models|
|`model-groups-selectable`| 1|0, if set to 0, selection of model groups is disallowed|
|`filedescription`|strValue, specifies the text displayed in the "filetype" field of the file dialog, e.g. "Textfile"|
|`fileextension`|strValue, specifies the extension for filenames, e.g. "**.txt".|
|`allowedmodeltypes`|strValue, contains model type names separated by ";"|
|`sortmode`|SortMode, specifies the order in which models are exported to the sgml file.|
|`no-submodels`|modifier, the dialogs's "Including referenced models" check box can be disabled.|
|`submodels`| 1|0, the checked state of that check box can be set.|
|`selmodelids`|strValue, a string containing the IDs of the selected models, separated by blank spaces.|
|`needsemptydir`| 1|0, allows to specify a restriction concerning the target directory. If specified (needsemptydir:1) then the export dialog can not be closed by pressing the "OK" button if the target directory is not empty.|

# Returns:  

|`ecode`|intValue, 1 if the user pressed the "OK" button, or 0 itf they pressed the "Cancel" button|
|`filename`|strValue, contains the filename the user entered in the export dialog. The file extension and the absolute path are added automatically.|
|`modelids`|strValue, contains a list of all the modelids (mainmodels and submodels) that the have been chosen in the export dialog.|
|`selmodelids`|strValue, contains only the mainmodels (=the models the user has selected).|
|`refmodelids`|strValue, contains only the submodels (=the models, that are referenced through the mainmodels).|

# Remarks:  
The option **sortmode** only applies if the checkbox "with referenced models" is checked in the export dialog. The models selected by the user in the export dialog are treated as mainmodels, the modeles referenced by the mainmodels are treated as submodels. If exporting with the option "Breadth-First Search", first all models directly referenced by the mainmodels are exported. Then all models directly referenced by the previously computed submodels are exported. If exporting with the option "Depth-First Search", for each referenced model, all submodels are exported before the next referenced model is treated.

![](/images/EXEC_EXPORTDIALOG.png)

If exporting the models of the example above in the mode "Breadth-First Search" (model A was selected in the export dialog and the checkbox "with referenced models" was checked), the models would be exported in the order A B C D E F G. If exporting in the mode "Depth-First Search", the order would be A B D E C F G.  
If exporting the models in the mode "Lexical Ordering", submodels will be ordered alphabetically (by model name).



# See Also:  



Example 1:

Starting an export dialog  
```adoscript
{% raw %}

#--- init global var storing the selection of models
IF (type (g_expDlgSelModels) = "undefined") {
    SETG g_expDlgSelModels:""
}
#--- here it comes
CC "Documentation" EXEC_EXPORTDIALOG
    "Documentation - choose your models..."
    filedescription:"Text file" fileextension:"**.txt"
    allowedmodeltypes:"Sample Model;Sample Static Model"
    sortmode:"Breadth-First Search" selmodelids:(g_expDlgSelModels)
IF (ecode = 0) {
    CC "AdoScript" INFOBOX "Dialog canceled!"
    EXIT
}
#--- save the selection of models
SET g_expDlgSelModels:(selmodelids)
#--- give a helpful information
CC "AdoScript" INFOBOX
    ("Models which are going to be exported: " + modelids)
#--- exporting starts here
# sth. like CC "Documentation" DOCU_EXPORT ...

{% endraw %}
```
{: .line-numbers}

The text displayed in the titlebar of the dialog window is set to "Documentation-choose your models...". The Description for the filetype is set to "Text file" and the extension is set to "txt". In the model list of the export dialog, only models of type "Sample Model" and "Sample Static Model" are listed. If the user pushes the cancel button, an INFOBOX is displayed and the script is exited. If the user pushes the OK button, all directly an indirectly selected modelids are displayed in an INFOBOX.

