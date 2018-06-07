---
layout: commandcall
category: CommandCall
title: "MODEL_SELECT_BOX"
tags: 1.3 1.5
---

MODEL_SELECT_BOX shows a dialog, where models, modelgroups or application models can be selected, either with single or with multi selection. If models shall be displayed, this can be either the currently loaded models or all models (of the current application library) which are stored in the database.

# Syntax:  

```adoscript
{% raw %}
CC "CoreUI" MODEL_SELECT_BOX [ opened-models | loaded-models ]
							[ multi-sel ]
							[ show-all-versions ]
							[ threads ]
							[ presel-modelids:strValue ]
							[ without-models ]
							[ mgroup-sel ] [ presel-mgroupids:strValue ]
							[ with-app-models ]
							[ SingleMTFilter | MultiMTFilter ]
							[ title:strValue ]
							[ boxtext:strValue ]
							[ oktext:strValue ]
							[ w:intValue h:intValue ]
							[ min-w:intValue min-h:intValue ]
							[ setdblclick:intValue ]
							[ extra:{ Extra } ] 

SingleMTFilter :	modeltype:strValue .

MultiMTFilter :	modeltype1:strValue modeltype2:strValue ... .

Extra  :	{ CheckBox } .

CheckBox :	CHECKBOX strValue [ checked:intValue ]
			result-var:varName .


# --> RESULT endbutton:strValue [ modelids:idList | threadids:idList ]
        [ mgroupids:idList ] [ appmodelids:idList ] [ extraValues ] .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`opened-models`|modifier, is specified, only models for which an own model window exist are displayed in the model select box.|
|`loaded-models`|modifier, is similar to opened-models, but here also models are included which are loaded at core level but which are not opened in an own model window, e.g. models which are shown as expanded submodels, embedded in a model window of another model.|
|`multi-sel`|modifier, if specified, the user can select multiple entries (models or modelgroups) in the treelistbox. If it is not specified, only one entry can be selected.|
|`show-all-versions`|modifier|
|`threads`|modifier, if specified in a versioned library, the user can only select each model threads. If it is not specified, for each model thread model versions can be selected separately. If  show-all-versions is specified, all model versions are displayed and expanded in the treelistbox when the model select box is opened.|
|`presel-modelids`|strValue, preselects threads or versions.|
|`without-models`|modifier, if specified, no models (but still model groups) are displayed in the model select box.|
|`mgroup-sel`|modifier, if specified, the user can also select modelgroups in the treelistbox. If not, only models can be selected. If the argument mgroup-sel is passed, modelgroups  can be preselected with the argument presel-modelgroupids.|
presel-mgroupids:strValue
|`with-app-models`|modifier, if given the model select box is built using the application models defined in the current library.|
|`SingleMTFilter`|modifier|
|`MultiMTFilter`|modifier|
|`title`|strValue, sets the dialog title|
|`boxtext`|strValue, the label of the treelistbox|
|`oktext`|strValue, he label of the ok-button.|
|`w`|intValue, the width of the dialog|
|`h`|intValue, the height of the dialog|
|`min-w`|intValue, the minimal width of the dialog|
|`min-h`|intValue, the minimal height of the dialog|
|`setdblclick`|intValue, allows to specify that if the user double clicks an item in the model select box, the dialog is not closed. If setdblclick is not given or the value is 1, the default behaviour takes place: Double clicking a model entry closes the dialog, double clicking a model groups shrinks or expands that group. If mgroup-sel is given, double clicking a model group will close the dialog with the model group as selection! Specifying setdblclick:0 avoids the above behaviour, as then any double click within the model select box does not close the dialog!|
|`modeltype`|strValue, the name of one modeltype can be specified. The model select box then only displays models of the specified modeltype.|
|`modeltypei`|strValue, with modeltype1, modeltype2, etc. the model select box can be restricted to models of multiple modeltypes.|
|`extra`|modifier; with it additional checkboxes can be inserted in the model select box. For each check box, the keyword CHECKBOX followed by the label of the checkbox has to be specified. Set the argument checked to 1 if the checkbox should be checked when the dialog is started, set it to 0 if not. For each checkbox, the name of a result variable is specified. After closing the dialog, the result variables are set to 1 if the checkbox has been checked, to 0 if not.|

# Returns:  

|`endbutton`|strValue, specifies which button has been pushed to close the dialog. If the user pushes the "OK" button, it is set to "ok". If he pushes "Cancel" it is set to "cancel".|
|`modelids`|idList, contains a blank separated list of model ids.|
|`threadids`|idList, contain a blank separated list of thread ids.|
|`mgroupids`|idList, contains a blank separated list of the ids of the selected modelgroups.|
|`appmodelids`|idList, contains a blank separated list of the ids of the selected application models.|
extraValues

# Remarks:

idList is a string value containing ids separated by " " (blank).

Threadids is used if the model select box was called with threads, otherwise modelids is used. T

# See Also:  



Example 1:

```adoscript
{% raw %}

...
CC "CoreUI" debug MODEL_SELECT_BOX
        oktext:"Hit Me!" boxtext:"Please select your models:"
        title:"MODEL_SELECTBOX example"  # without 2nd "_", hehe...
        multi-sel mgroup-sel
        extra:{
                CHECKBOX "Option 1" checked:1 result-var:option1 
                CHECKBOX "Option 2" result-var:option2
        }
CC "AdoScript" INFOBOX
        ("Option1 = " + STR option1 + "\n" +
         "Option2 = " + STR option2)

{% endraw %}
```
{: .line-numbers}

![](/images/MODEL_SELECT_BOX.png)

Example 2:

The following commands shows the application models without the attached bp and we models. Exactly one application model can be selected.  
```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX
        with-app-models mgroup-sel without-models
IF (endbutton = "ok") {
    # appmodelids is a string containing exactly one id
    SET appmodelid:(VAL appmodelids)
    # ...
}

{% endraw %}
```
{: .line-numbers}
