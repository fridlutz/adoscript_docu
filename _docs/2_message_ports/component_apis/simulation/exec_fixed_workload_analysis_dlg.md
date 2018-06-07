---
layout: commandcall
category: CommandCall
title: "EXEC_FIXED_WORKLOAD_ANALYSIS_DLG"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Simulation" EXEC_FIXED_WORKLOAD_ANALYSIS_DLG
												[ auto-read-only: 1|0 ]
												[ auto-close: 1|0 ]
												[ auto-component: 1|0 ]
												[ randseed:intValue ] 
												[ programcalls: 1|0 ]
												[ activity-analysis: 1|0 ]
												[ calculation: 1|0 ]
												[ animation: 1|0 ]
												[ ProtocolSettings ]
												[ simoption:intValue ]
												[ day-1:intValue ]
												[ month-1:intValue ]
												[ day-2:intValue ]
												[ month-2:intValue ]
												[ year-2:intValue ]
												[ day-3:intValue ]
												[ month-3:intValue ]
												[ year-3:intValue ]
												[ appmodelname:strValue ]
												[ no-error-messages: 1|0 ] 

ProtocolSettings:	protocol:none | short-format | long-format
					[ protfile:strValue ]

#--> RESULT ecode:intValue 
			errmsg:strValue 
			canceled: 1|0
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`auto-read-only`|Sets an automated answer to the query about models being loaded in read-only mode. The query will not be displayed to the user. If "auto-save-results" is activated, there will still appear an error message, if some models are in read-only mode when saving the results is attempted.|
|`auto-close`|Sets an automated answer to the query about models being closed after the simulation. The query will not be displayed to the user.|
|`auto-component`|Sets an automated answer to the query about passive simulation components being disabled. The query will not be displayed to the user.|
|`randseed`|Default randseed-value for the deterministic simulation.|
|`programcalls`|Sets a default value for the passive simulation component "programcalls". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is 0 (off).|
|`activity-analysis`|Sets a default value for the passive simulation component "activity analysis". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is 1 (on).|
|`calculation`|Sets a default value for the passive simulation component "calculation". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is 1 (on).|
|`animation`|Sets a default value for the passive simulation component "animation". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is 1 (on).|
|`protocol`|Sets a default value for the passive simulation component "simulation protocol". Allowed values are none (no protocol is generated), short-format (short format protocol) and long-format (long format protocol). Default = none.|
|`protfile`|Path to the protocol file.|
|`simoption`|Default simOption ("Input parameter combination") to be used for the simulation. Domain: [1-n]|
|`day-1`|Default simulation begin day.|
|`month-1`|Devault simulation begin moth.|
|`day-2`|Default calculation begin day.|
|`month-2`|Default calculation begin month.|
|`year-2`|Default calculation begin year.|
|`day-3`|Default calculation end day.|
|`month-3`|Default calculation end month.|
|`year-3`|Default calculation end year.|
|`no-error-messages`|If set to 1 then no simulation error messages will be displayed. If an error occurs, the simulation is simply aborted and the error message is returned in the return value errmsg.|
|`appmodelname`|Default application model name.|

# Returns:  

|`ecode`|intValue, 0 for success or 1 if the dialog was canceled or an error occured|
|`errmsg`|strValue, holds the error message of the last (if any) simulation-error that occured. This message is the same text that is usually displayed to the user in an ErrorBox.|
|`canceled`|1|0, reports whether the start dialog of the simulation has been canceled. It does not report whether the user did cancel at any other point of the simulation.|

# Remarks:



# See Also:  



Example:


