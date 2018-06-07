---
layout: commandcall
category: CommandCall
title: "RUN_DYNAMIC_EVALUATION"
tags: 1.3 1.5
---

The command RUN_DYNAMIC_EVALUATION runs the specified "Dynamic Evaluation Module".

This command will only work correctly in application libraries with time-based versioning!

# Syntax:  

```adoscript
{% raw %}
CC "Evaluation" RUN_DYNAMIC_EVALUATION strValue
											appmodelid:intValue
											[ hpd:realValue ]
											[ dpy:realValue ]
											[ runs:intValue ]
											[ randseed:1|0 ]
											[ volume-check:1|0 ]
											start:strValue end:strValue
											[ checkhist ]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the evaluation module.|
|`applmodel`|strValue, (Default) name of the application model which shall be evaluated.|
|`hpd`|realValue, hours per day (floating value). If not given, the latest used value is used.|
|`dpy`|realValue, days per year (floating value). If not given, the latest used value is used.|
|`runs`|intValue, number of simulation runs. If not given, the latest used value is used.|
|`randseed`|1|0, do simulation with random seeds? (Default = 0, meaning that simulation is performed with fixed seeds, producing always the same results.)|
|`start`|strValue, start evaluation period (long format).|
|`end`|strValue, end evaluation period (long format). Has to be &gt;= start period.|
|`volume-check`|1|0, if set to 1 (= default) all models which refere to volumes from previous periods are reported. (Usually it is an error in the models, if a model uses a volume from a previous period.)|
|`checkhist`|modifier, if given, a check is performed before the evaulation wether all models are "historized" (= wether all models are set to read-only in the model attribute "access state").|

# Returns:  

|`ecode`|intValue, is set to 0 if everything worked or 1 if there was an error or if the user canceled|

# Remarks:

No start dialog is displayed to the user, all settings have to be passed as parameters of the command.

# See Also:  

[EXEC_DYNAMIC_EVAL_START_DLG](exec_dynamic_eval_start_dlg.html "EXEC_DYNAMIC_EVAL_START_DLG")  
[EXEC_DYNAMIC_EVAL_MODULE_DLG](exec_dynamic_eval_module_dlg.html "EXEC_DYNAMIC_EVAL_MODULE_DLG")  


Example:


