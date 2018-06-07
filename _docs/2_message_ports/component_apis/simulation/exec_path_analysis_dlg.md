---
layout: commandcall
category: CommandCall
title: "EXEC_PATH_ANALYSIS_DLG"
tags: 1.3 1.5
---

This command executes the path analysis start dialog.

# Syntax:  

```adoscript
{% raw %}
CC "Simulation" EXEC_PATH_ANALYSIS_DLG
									[ modelid:intValue ]
									[ runs:intValue ]
									[ dpy:realValue ]
									[ hpd:realValue ]
									[ simoption:intValue ]
									[ auto-read-only: 1|0  ]
									[ auto-close:1|0 ]
									[ auto-loop:1|0 ]
									[ setLoopDetectionCount:intValue ]
									[ randseed:intValue ]
									[ programcalls:1|0 ]
									[ no-error-messages:1|0 ]
									[ loaded-models:1|0 ]

#--> RESULT ecode:intValue
			errmsg:strValue 
			canceled:boolValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the default model ID|
|`runs`|intValue, number of simulation runs|
|`dpy`|realValue, default days per year|
|`hpd`|realValue, default hours per day|
|`simoption`|intValue, number of the SimMapping option to be used [1 .. n]. If not given, the default (e.g. from the last simulation) will be used. If a too small value (&lt;= 0) is passed, 1 is assumed.|
|`auto-read-only`| 1|0, sets an automated answer to the query about models being loaded in read-only mode. The query will not be displayed to the user.|
|`auto-close`|1|0, sets an automated answer to the query about models being closed after the simulation. The query will not be displayed to the user.|
|`auto-loop`|1|0, sets an automated answer to the query about continuing simulation although a probably endless loop was detected. The query will not be displayed to the user. (Note: If the simulation is unable to continue because of an endless loop exhausting the available system resources, a Windows system error message will still be displayed. Afterwards ADOxx may crash because of missing system resources.)|
|`setLoopDetectionCount`|intValue, sets the number of subsequent objects within one process instance which indicate that an endless loop has to be assumed. If no count is given, the standard value 5000 ist used. Note that loop detection is only performed during path analysis and volume analysis, not during workload analysis.|
|`randseed`|intValue, default randseed-value for the deterministic simulation.|
|`programcalls`|1|0, sets a default value for the passive simulation component "programcalls". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is 0 ("off").|
|`no-error-messages`|1|0, if set to 1 then no simulation error messages will be displayed. If an error occurs, the simulation is simply aborted and the error message is returned in the return value errmsg.|
|`loaded-models`|1|0, if set to 1 only loaded models are displayed by default in the model selection box. If set to 0 all models are displayed there. If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is 0 ("off").|

# Returns:  

|`ecode`|intValue, 0 for success or 1 if the dialog was canceled or an error occured|
|`errmsg`|strValue, holds the error message of the last (if any) simulation-error that occured. This message is the same text that is usually displayed to the user in an ErrorBox.|
|`canceled`|1|0, reports whether the start dialog of the simulation has been canceled. It does not report whether the user did cancel at any other point of the simulation.|

# Remarks:

After the Path Analysis the result value is returned immediately after the opening of the simulation result window. Your AdoScript will therefore continue immediately,  even before the simulation result window has been closed.

Since ADOxx 1.2 it is possible to continue with AdoScript-commands also only after closing the simulation result window: The AdoScript has to be separated into two parts. The first part ends with the start of the path analysis. The second part contains the code that shall be executed once the result window has been closed. It is placed in the handler of the AdoScript event "&lt;SimulationEnded&gt;" .

# See Also:  

[SimulationEnded](simulationended.html "SimulationEnded")  
[RUN_PATH_ANALYSIS](run_path_analysis.html "RUN_PATH_ANALYSIS")  


