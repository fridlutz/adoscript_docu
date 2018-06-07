---
layout: commandcall
category: CommandCall
title: "RUN_ANALYTIC_EVALUATION"
tags: 1.3 1.5
---

Is a command call of the message port "Analysis" that executes the analytic evaluation without showing the start dialog.

!!! Command NOT working !!!  

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" RUN_ANALYTIC_EVALUATION modelid:intValue
										[ dpy:intValue ]
										[ hpd:intValue ]
										[ volume:intValue ]
										[ simoption:intValue ]
										[ accuracy:intValue ]
										[ maxlooplen:intValue ]
										[ maxpaths:intValue ]
										[ auto-close: 1|0 ]
										[ no-result-window ]
										[ auto-save-results ]
										[ no-error-messages: 1|0 ] .
										
# -->	RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, ID of the model to be simulated.|
|`dpy`|intValue, working days per year. If not given, the default (e.g. from the last simulation) will be used. There is no check done, wether dpy &lt;= 365.|
|`hpd`|intValue, orking hours per day. If not given, the default (e.g. from the last simulation) will be used. There is no check done, whether hpd &lt;= 24.|
|`volume`|intValue, process volume. If not given, the default will be used.|
|`simoption`|intValue, number of the SimMapping option to be used [1 .. n-1]. If not given, the default (e.g. from the last simulation) will be used. If a too small value (&lt;= 0) is passed, 1 is assumed. If a too large value is passed, an error message will be displayed.|
accuracy - intValue, value for accuracy (1 - 100).
|`maxlooplen`|intValue, value for max loop length.|
|`maxpaths`|intValue, value for max paths.|
|`auto-close`| 1|0, sets an automated answer to the query about models being closed after the simulation. The query will not be displayed to the user. (If the models need to be saved before closing them, the user will still be asked if that shall be done.)|
|`no-result-window`|modifier, if given, no result window will be displayed.|
|`auto-save-results`|modifier, if given, the simulation results (under consideration of the volume in the process start) will automatically be saved to the models after the analytical evaluation. (If any models have to be loaded before the evaluation, they will be loaded with write-access. If this is not possible, the evaluation will be terminated with the error message [aanaeval-07].) If the volume in the process start is "0" then the simulation results will be saved for one process instance (assuming a volume of "1"). This was requested by "Barmer EK".|
|`no-error-messages`| 1|0|

# Returns:  

|`ecode`|intValue|
|`errmsg`|strValue|

# Remarks:

The result value ecode is either 0 (meaning success) or 1 (= error or dialog was canceled by user).  
The result value errmsg holds the error message of the last (if any) error that occured. This message is the same text that is usually displayed to the user in an ErrorBox. Please note that the text may differ for different ADOxx version.

# See Also:  

[ANALYSIS_BROWSER](analysis_browser.html "ANALYSIS_BROWSER")  
[EXECUTE_USER_ANALYSIS_QUERY](execute_user_analysis_query.html "EXECUTE_USER_ANALYSIS_QUERY")  
[EXEC_ANALYTIC_EVALUATION_START_DLG](exec_analytic_evaluation_start_dlg.html "EXEC_ANALYTIC_EVALUATION_START_DLG")  
[EVALUATE_QUERY](evaluate_query.html "EVALUATE_QUERY")  


