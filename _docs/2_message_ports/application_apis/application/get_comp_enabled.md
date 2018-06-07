---
layout: commandcall
category: CommandCall
title: "GET_COMP_ENABLED"
tags: 1.3 1.5
---

Calling GET_COMP_ENABLED returns for component with id intValue the string "OK" when it is enabled, an empty string when not.

# Syntax:  

```adoscript
{% raw %}
SEND "GET_COMP_ENABLED 2" to:"Application" answer:enabled

#-->	strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`<main_return_value>`|intValue, "OK" when enabled, empty string otherwise.|

# Remarks:

The following list tells the ids for each component  
*Acquisition	1	(see COMP_acq.png)
*Modeling	2	(see COMP_mod.png)
*Analysis	3	(see COMP_ana.png)
*Simulation	4	(see COMP_sim.png)
*Evaluation	5	(see COMP_eva.png)
*ImportExport	6	(see COMP_imp.png)

# See Also:  



Example 1:

GET_COMP_ENABLED is called to check if the modeling component is enabled. If not, an infobox is displayed and it is enabled. Call the example twice, once as is and a second time without the '#' character in the first line.  
```adoscript
{% raw %}

CC "Application" DISABLE_COMP modeling

SEND "GET_COMP_ENABLED 2" to:"Application" answer:enabled
IF (enabled != "OK")
{
   CC "AdoScript" INFOBOX "The modeling component is not enabled!"
   CC "Application" ENABLE_COMP modeling
}

{% endraw %}
```
{: .line-numbers}

