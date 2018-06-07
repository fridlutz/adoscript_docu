---
layout: commandcall
category: CommandCall
title: "GET_ACTIVE_COMP"
tags: 1.3 1.5
---

Calling GET_ACTIVE_COMP returns the id of the currently active component.  


# Syntax:  

```adoscript
{% raw %}
SEND "GET_ACTIVE_COMP" to:"Application" answer:id

#--> RETURN	intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`<main_return_value>`|intValue, Contains the id of the active component.|

# Remarks:

The following list tells the ids for each component  
* Acquisition	1	(see COMP_acq.png)
* Modeling	2	(see COMP_mod.png)
* Analysis	3	(see COMP_ana.png)
* Simulation	4	(see COMP_sim.png)
* Evaluation	5	(see COMP_eva.png)
* ImportExport	6	(see COMP_imp.png)

# See Also:  



Example 1:

Returns the currently opened component and prints the id in an infobox.  
```adoscript
{% raw %}

SEND "GET_ACTIVE_COMP" to:"Application" answer:id
CC "AdoScript" INFOBOX ("The current component has the id " + id)

{% endraw %}
```
{: .line-numbers}

