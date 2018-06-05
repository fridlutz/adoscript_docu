---
layout: commandcall
category: CommandCall
title: "RUN_MODEL_NUMBERING"
tags: 1.3 1.5
---

RUN_MODEL_NUMBERINGR uns the numbering of all objects in the model with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" RUN_MODEL_NUMBERING modelid:intValue
								  [ no-result-window:boolValue ] .


boolValue:	1 | 0


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`no-result-window`|boolValue|

# Returns:  

|`ecode`|intValue, the resulting ecode is either 0 (no error) or 1 (error)|



# Remarks:

If the optional parameter no-result-window is set to 1 then no result window (= a dialog stating which object could be numbered and which could not be numbered) will be displayed.

Note that it is not possible yet to suppress error messages which may be displayed during the enumeration because of invalid models.

# See Also:  



Example 1:

```adoscript
{% raw %}

# Get the model id of the currently active model:
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
SET n_mid:(VAL modelid)

# Number the objects in the model:
CC "Modeling" RUN_MODEL_NUMBERING modelid:(n_mid) no-result-window:1
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "[enumeration-01]\nBeim Nummerieren der Objekte ist ein unerwarteter Fehler aufgetreten." title:"Error"
}

{% endraw %}
```
{: .line-numbers}
This AdoScript runs the model enumeration function in the currently active model without showing any result window.  
So if the enumeration is successful, it is done completely silently.  
If an error occures, first the error box of the enumeration function is displayed (this can not be suppressed yet). Then the AdoScript opens its own error box showing the error message [enumeration-01].

