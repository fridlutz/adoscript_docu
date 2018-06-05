---
layout: commandcall
category: CommandCall
title: "EXEC_ANALYTIC_EVALUATION_START_DLG"
tags: 1.3 1.5
---

Is a command call of the message port "Analysis" that executes the analytic evaluation start dialog.

!!! Command NOT working !!!  

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" EXEC_ANALYTIC_EVALUATION_START_DLG [ modelid:intValue ] 
													[ dpy:intValue ] 
													[ hpd:intValue ] 
													[ simoption:intValue ] 
													[ accuracy:intValue ] 
													[ maxlooplen:intValue ] 
													[ maxpaths:intValue ] 
													[ auto-close: "yes" | "no" ] 
													[ no-result-window ] 
													[ auto-save-results ]
													
# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model to be evaluated.|
|`dpy`|intValue, working days per year. If not given, the default (e.g. from the last simulation) will be used. There is no check done, wether dpy &lt;= 365.|
|`hpd`|intValue, working hours per day. If not given, the default (e.g. from the last simulation) will be used. There is no check done, wether 	hpd &lt;= 24.|
|`simoption`|intValue, number of the SimMapping option to be used [1 .. n-1]. If not given, the default (e.g. from the last simulation) will be used. If a too small value (&lt;= 0) is passed, 1 is assumed.|
If too large a value is passed, an error message will be displayed.
accuracy - intValue, default value for accuracy (1 - 100).
|`maxlooplen`|intValue, default value for max loop length.|
|`maxpaths`|intValue, default value for max paths.|
|`auto-close`|boolValue, sets an automated answer to the query about models being closed after the simulation. The query will not be displayed to the user.|
|`no-result-window`|modifier, if given, no result window will be displayed.|
|`auto-save-results`|modifier, if given, the simulation results (under consideration of the volume in the process start) will automatically be saved to the models after the analytical evaluation. (If any models have to be loaded before the evaluation, they will be loaded with write-access. If this is not possible, the evaluation will be terminated with the error message [aanaeval-07].)|

# Returns:  

|`ecode`|intValue|

# Remarks:



# See Also:  

[ANALYSIS_BROWSER](analysis_browser.html "ANALYSIS_BROWSER")  
[EXECUTE_USER_ANALYSIS_QUERY](execute_user_analysis_query.html "EXECUTE_USER_ANALYSIS_QUERY")  
[EVALUATE_QUERY](evaluate_query.html "EVALUATE_QUERY")  
[RUN_ANALYTIC_EVALUATION](run_analytic_evaluation.html "RUN_ANALYTIC_EVALUATION")  



