---
layout: commandcall
category: CommandCall
title: "OPEN"
tags: 1.3 1.5
---

OPEN opens models in the modeling editor.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" OPEN modelids:strValue [ with-submodels ] [ write-protected ] [ minimized ] .


# --> RESULT ecode:intValue opened:strValue invalid:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelids`|strValue, a list of model ids (separated by spaces) for the models that should be opened is passed in modelids.|
|`with-submodels`|modifier, by passing the argument with-submodels also models referenced by the specified models will be opened.|
|`write-protected`|modifier, by passing the argument write-protected the models are opened writre protected.|
|`minimized`|modifier, by passing the argument minimized, all opened models windows are minimized.|

# Returns:  

|`ecode`|intValue, the return value ecode is set to 0 when the models could be opened, to 1 if errors occured.|
|`opened`|strValue,  the return variable opened contains a list of model ids that have been opened.|
|`invalid`|strValue, the return variable invalid contains a list of model ids that could not be opened.|

# Remarks:

Do not confuse with CC "Core" LOAD_MODEL! "OPEN" opens the model the same way a user would do while "LOAD_MODEL" loads the model only into the core (which is faster of course.)


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_MODEL_ID modelname:"Testmodel" modeltype:"Sample Model"
CC "Modeling" OPEN modelids:(STR modelid)

{% endraw %}
```
{: .line-numbers}
Opens the model called "Testmodel" of type "Sample Model". Either create such a model before you execute the example or adjuste modelname and modeltype in the example so that an existing model is opened.

