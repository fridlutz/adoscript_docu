---
layout: commandcall
category: CommandCall
title: "EXEC_DYNAMIC_EVAL_START_DLG"
tags: 1.3 1.5
---

The command EXEC_DYNAMIC_EVAL_START_DLG executes the start dialog for the "Dynamic Evaluation Modules" and returns the settings which the user has selected.

# Syntax:

```adoscript
{% raw %}
CC "Evaluation" EXEC_DYNAMIC_EVAL_START_DLG strValue
											[ appmodelid:intValue ]
											[ hpd:realValue ]
											[ dpy:realValue ]
											[ runs:intValue ]
											[ randseed:1|0 ]
											[ start:strValue end:strValue ]

#--> RESULT ecode:intValue 
			canceled:1|0 
			appmodelid:intValue appmodelname:strValue 
			hpd:realValue dpy:realValue 
			runs:intValue randseed:1|0 
			start:strValue end:strValue			
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the evaluation module.|
|`applmodel`|strValue, (Default) ID of the application model which shall be preselected in the dialog.|
|`hpd`|realValue, hours per day (floating value).|
|`dpy`|realValue, days per year (floating value).|
|`runs`|intValue, number of simulation runs.|
|`randseed`|1|0, do simulation with random seeds? (Default = 0, meaning that simulation is performed with fixed seeds, producing always the same results.)|
|`start`|strValue, start evaluation period (long format).|
|`end`|strValue, end evaluation period (long format). Has to be &gt;= start period.|

# Returns:  

|`ecode`|intValue, is set to 0 if everything worked; If there was an error (or if the user canceled) 1 is returned.|
|`canceled`|1|0 , is set to 1 if the user canceled the start dialog.|
|`appmodelid`|intValue, ID of application model selected by the user.|
|`appmodelname`|strValue, name of application model selected by user.|
|`hpd`|realValue, hours per day|
|`dpy`|realValue, days per year|
|`runs`|intValue, number of selected simulation runs.|
|`randseed`|1|0, use random seeds?|
|`start`|strValue, start evaluation period (long format).|
|`end`|strValue, end evaluation period (long format).|

# Remarks:

This command will only work correctly in application libraries with time-based versioning!

# See Also:  

[EXEC_DYNAMIC_EVAL_MODULE_DLG](exec_dynamic_eval_module_dlg.html "EXEC_DYNAMIC_EVAL_MODULE_DLG")  
[RUN_DYNAMIC_EVALUATION](run_dynamic_evaluation.html "RUN_DYNAMIC_EVALUATION")  


Example:

