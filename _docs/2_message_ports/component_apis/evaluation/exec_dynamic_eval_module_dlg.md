---
layout: commandcall
category: CommandCall
title: "EXEC_DYNAMIC_EVAL_MODULE_DLG"
tags: 1.3 1.5
---

The command EXEC_DYNAMIC_EVAL_MODULE_DLG executes the start dialog for the "Dynamic Evaluation Modules" and runs the evaluation afterwards.

This command will only work correctly in application libraries with time-based versioning!

# Syntax:

```adoscript
{% raw %}
CC "Evaluation" EXEC_DYNAMIC_EVAL_MODULE_DLG strValue
											[ applmodel:strValue ]
											[ hpd:realValue ]
											[ dpy:realValue ]
											[ runs:intValue ]
											[ randseed:1|0 ]
											[ start:strValue end:strValue ]
											[ volume-check:1|0 ]
											[ checkhist ] .

# --> RESULT ecode:intValue canceled:1|0
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the evaluation module.|
|`applmodel`|strValue, (Default) name of the application model which shall be evaluated. (The user can change this in the start dialog.)|
|`hpd`|realValue, (Default) hours per day (floating value).|
|`dpy`|realValue, (Default) days per year (floating value).|
|`runs`|intValue, (Default) number of simulation runs.|
|`randseed`|1|0, do simulation with random seeds? (Default = 0, meaning that simulation is performed with fixed seeds, producing always the same results.)|
|`start`|strValue, (Default) start evaluation period (long format).|
|`end`|strValue, (Default) end evaluation period (long format). Has to be &gt;= start period.|
|`volume-check`|1|0, if set to 1 (= default) all models which refere to volumes from previous periods are reported. (Usually it is an error in the models, if a model uses a volume from a previous period.)|
|`checkhist`|modifier, if given, a check is performed before the evaulation wether all models are "historized" (= wether all models are set to read-only in the model attribute "access state").|

# Returns:  

|`ecode`|intValue, is set to 0 if everything worked or 1 if there was an error or if the user canceled|
|`canceled`|1|0, is set to 1 if the user canceled the start dialog.|

# Remarks:



# See Also:  

[EXEC_DYNAMIC_EVAL_START_DLG](exec_dynamic_eval_start_dlg.html "EXEC_DYNAMIC_EVAL_START_DLG")  
[RUN_DYNAMIC_EVALUATION](run_dynamic_evaluation.html "RUN_DYNAMIC_EVALUATION")  


Example 1:

```adoscript
{% raw %}

CC "Evaluation" EXEC_DYNAMIC_EVAL_MODULE_DLG "Capacity management" period:("March 2001") checkhist

{% endraw %}
```
{: .line-numbers}

This command executes the start dialog for the evaluation module "Capacity management" (which must be already customized). As default evaluation period "March 2001" is preselected. All evaluated models are checked for being "historized" before evaluation starts.  
