---
layout: commandcall
category: CommandCall
title: "CHECK_CARDINALITIES"
tags: 1.3 1.5
---

CHECK_CARDINALITIES checks cardinalities of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CHECK_CARDINALITIES [ modelid:intVal ] [ silent ] [ nosuccessmessage ] .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intVal|
|`silent`|modifier|
|`nosuccessmessage`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The model to be checked has to be loaded and opened in the modeling window, the id of the model is specified with modelid. If no modelid has been specified, the cardinalities of the current active model are checked.

When errors are encountered, an error box is displayed and the wrong connectors are marked (see example below). When passing the argument silen, no error messages are displayed.

When no errors aoccur, a success message is displayed. The success message can be hidden by passing the argument nosuccessmessage.  
![](/images/CHECK_CARDINALITIES.png)

The return variable ecode contains the value 0 if no errors were found, the value 1 if errors occured.  
# See Also:  



Example 1:

```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX multi-sel
CC "Modeling" OPEN modelids:(modelids)
SETG success:1
FOR modid in:(modelids)
{
   CC "Modeling" CHECK_CARDINALITIES modelid:(VAL modid) silent nosuccessmessage
   IF (ecode > 0)
   {
      SETG success:0
   }
}
CC "Modeling" CLOSE_ALL
IF (success = 0)
{
   CC "AdoScript" INFOBOX "Cardinality errors have been detected!"
}
ELSE
{
   CC "AdoScript" INFOBOX "All selected models have correct cardinalities!"
}

{% endraw %}
```
{: .line-numbers}
Lets the user select a number of models. All selected models are opened, cardinalities are checked (without displaying error and success messages) and then the models are closed again. If cardinality errors occured in any model, an infobox with an error message is displayed. If no errors occured, a success message is displayed.

