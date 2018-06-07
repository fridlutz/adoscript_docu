---
layout: commandcall
category: CommandCall
title: "RUN_VOLUME_ANALYSIS"
tags: 1.3 1.5
---

RUN_VOLUME_ANALYSIS executes the Volume Analysis (2nd simulation algorithm, aka Static Assignment) without showing its start dialog.

# Syntax:  

```adoscript
{% raw %}
CC "Simulation" RUN_VOLUME_ANALYSIS	appmodelname:strValue
									[ runs:intValue ]
									[ dpy:intValue ]
									[ hpd:intValue ]
									[ simoption:intValue ]
									[ adopt-results:ResultPeriodType ]
									[ auto-read-only:boolValue ]
									[ auto-close:boolValue ]
									[ auto-volume:boolValue ]
									[ auto-component:boolValue ]
									[ auto-loop:boolValue ]
									[ setLoopDetectionCount:intValue ]
									[ randseed:intValue ] 
									[ programcalls:boolValue ]
									[ path-analysis:boolValue ]
									[ calculation:boolValue ]
									[ protocol:ProtocolType ]
									[ protfile:strValue ]
									[ no-error-messages:boolValue ] 
									[ no-result-window ] 
									[ process-results:{ ResultProcessingJobList } ]

ProtocolType :		none | short-format | long-format .

ResultProcessingJobList :	{ ResultProcessingJob } .

ResultProcessingJob :	JOB mode:ResultMode [ classid:id relationclassid:id ]
											period-type:ResultPeriodType
											[ handler:procedureName ] [ show-browser ] .

ResultMode :	"process-related" | "person-related" |
				"we-related" | "capacity-planning" |
				"resource-process-related" | "resource-related" | "resource-we-related" .

ResultPeriodType :		"null" | "per-process" | "per-month" | "per-year" .

#-->RESULT ecode:intValue errmsg:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`appmodelname`|Name of the application model.|
|`runs`|Number of simulation runs. If not specified, the default (e.g. from the last simulation) will be used.|
|`dpy`|Working days per year. If not specified, the default (e.g. from the last simulation) will be used. There is no check done wether dpy &lt;= 365.|
|`hpd`|Working hours per day. If not specified, the default (e.g. from the last simulation) will be used. There is no check done wether hpd &lt;= 24.|
|`simoption`|Number of the SimMapping option to be used [1 .. n]. If not given, the default (e.g. from the last simulation) will be used. If a too small value (&lt;= 0) is passed, 1 is assumed. If a too large value is passed, an error message will be displayed.|
|`adopt-results`|If not set to null, the simulation result values are being saved into the models after simulation. Before simulation, models of the application model which are not already loaded are automatically being loaded writeable. These models are not being closed after the simulation. If any of the relevant models is loaded write protected, the execution stops with an error. If the result window is not suppressed (i.e. no-result-window is not specified), using result adoption will be effective before the result window appears. Note that this has to be confirmed by the user. If set to null, models which are not already loaded are loaded write protected and these models are being closed after the simulation. The simulation will not modify any model. Default: null (no adoption).|
|`auto-read-only`|Sets an automated answer to the query about models being loaded in read-only mode. The query will not be displayed to the user. If set to 0, and one of the relevant models is loaded write protected, the execution will stop with an error. If set to 1, the simulation shall be executed regardless of models being write protected. If adopt-results is set to anything but null and any of the relevant models is loaded write protected, then the execution will stop with an error, even if auto-read-only is set to 1. So auto-read-only is meaningless in that case.|
|`auto-close`|Sets an automated answer to the query about models being closed after the simulation. The query will not be displayed to the user. If set to 0, all models stay loaded. If set to 1, models which have automatically been loaded write protected, are being closed. If adopt-results is set to anything but null, then models have been loaded writeable, have been modified and are not being closed. So auto-close is meaningless in that case.|
|`auto-volume`|Sets an automated answer to the query about no volume being specified in a process model. The query will not be displayed to the user.|
|`auto-component`|Sets an automated answer to the query about passive simulation components being disabled. The query will not be displayed to the user.|
|`auto-loop`|Sets an automated answer to the query about continuing simulation although a probably endless loop was detected. The query will not be displayed to the user. (Note: If the simulation is unable to continue because of an endless loop exhausting the available system resources, a Windows system error message will still be displayed. Afterwards ADOxx may crash because of missing system resources.)|
|`setLoopDetectionCount`|Sets the number of subsequent objects within one process instance which indicate that an endless loop has to be assumed. If no count is given, the standard value 5000 ist used. Note that loop detection is only performed during path analysis and volume analysis, not during workload analysis.|
|`randseed`|Default randseed-value for the deterministic simulation.|
|`programcalls`|Sets a default value for the passive simulation component "programcalls". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is: 0 (off).|
|`path-analysis`|Sets a default value for the passive simulation component "path analysis". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is: 1 (on).|
|`calculation`|Sets a default value for the passive simulation component "calculation". If this parameter is not given, the last value (from previous simulatio runs) will be used. If no simulation was performed previously, then the default value is: 1 (on).|
|`protocol`|Sets a default value for the passive simulation component "simulation protocol". Allowed values are none (no protocol is generated), short-format (short format protocol) and long-format (long format protocol). Default: none.|
|`protfile`|Path to the protocol file.|
|`no-error-messages`|If set to 1, no simulation error messages will be displayed. If an error occurs, the simulation is simply aborted and the error message is returned via the result value errmsg.|
|`no-result-window`|If this option is specified, the simulation results window is suppressed. Otherwise your AdoScript program is paused until the user closes the simulation results window.|
|`process-results`|Here you can specify a list of result processing jobs. Each job generates results.|

The results are of a certain result type (mode) and a certain result period type (period-type). If the result type is we-related, capacity-planning or resource-we-related, then additionally a class and a relation class have to be specified for the result generation (classid, relationclassid). You can specify a callback procedure (handler), which is called with the generated results as parameter. This procedure must have exactly one parameter results:array. The passed array has two dimensions and contains all cells of the result table, inclusive column headers, as string values. See example 2 for a usage of a callback procedure. If show-browser is specifyed, a browser window is being shown, which contains the result table.


# Returns:  

|`ecode`|0 |1 , 0 meaning success and 1 meaning error or cancel.|
|`errmsg`|strValue, holds the error message of the last (if any) simulation-error that occured. This message is the same text that is usually displayed to the user in an ErrorBox.|

# Remarks:

Any user interaction, which normally would happen before, during and after the simulation run, can be bypassed by specifying options. So the simulation can be run completely without being paused by a query or an error box. Even the simulation results dialog can be suppressed. The simulation results can therefore be processed by your AdoScript program.


# See Also:  



Example 1 (Running the simultation without any user interaction):

At first, let the variable appmodelname be set, e.g. by using a model select box  
```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX with-app-models mgroup-sel without-models
CC "Core" GET_APPMODEL_INFO appmodelid:(VAL appmodelids)

{% endraw %}
```
{: .line-numbers}

The following command lets the simulation run without asking the user for parameters  
```adoscript
{% raw %}

CC "Simulation" RUN_VOLUME_ANALYSIS
        appmodelname:(appmodelname)
        adopt-results:"per-process" no-result-window 

{% endraw %}
```
{: .line-numbers}

However, if an error occours, your AdoScript program will be paused because an error box will be shown. Also, if no volume is specified in a process model, if passive simulation components are disabled, or if a probably endless loop is detected, your AdoScript program will wait for an ackknowledgement by the user.  
If you are not sure whether all conditions for a successful simulation are satisfied or not, but you want to ensure that the AdoScript program will not be paused, you may add options to suppress query and eror boxes:  
```adoscript
{% raw %}

CC "Simulation" RUN_VOLUME_ANALYSIS
        appmodelname:(appmodelname)
        adopt-results:"per-process" no-result-window
        auto-volume:1 auto-component:1 auto-loop:1
        no-error-messages:1
		
{% endraw %}
```
{: .line-numbers}

Example 2 (Running the simultation with result processing) :  
We take the CC from the end of example 1, remove the result adoption and add a callback for result processing  
```adoscript
{% raw %}

CC "Simulation" RUN_VOLUME_ANALYSIS
        appmodelname:(appmodelname)
        adopt-results:"per-process" no-result-window
        auto-volume:1 auto-component:1 auto-loop:1
        process-results:{
            JOB mode:"process-related" period-type:"per-process"
                handler:"PROCESS_RESULTS"
        }

# callback procedure for JOB in RUN_VOLUME_ANALYSIS
# results is a two-dimensional array of strings
PROCEDURE PROCESS_RESULTS results:array {
    # we produce a csv text -info- which is being shown at the end
    # (csv = "comma separated value")
    SETL info:""
    # for each each row of the results
    FOR rowindex from:0 to:(LEN results - 1) {
        SET row:(results[rowindex])
        # for each column of current row
        FOR colindex from:0 to:(LEN row - 1) {
           # append ";" if not first col
           IF (colindex) {
               SET info:(info + ";")
           }
           # append current cell
           SET info:(info + (row[colindex]))
        }
        # append newline
        SET info:(info + "\n")
    }
    # show csv text in an infobox
    CC "AdoScript" INFOBOX (info)
}

{% endraw %}
```
{: .line-numbers}

