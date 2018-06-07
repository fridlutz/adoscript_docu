---
layout: commandcall
category: CommandCall
title: "SET_ACTIVE_COMP"
tags: 1.3 1.5
---

With the command SET_ACTIVE_COMP the current component can be changed in the Modelling Toolkit.

# Syntax:  

```adoscript
{% raw %}
CC "Application" SET_ACTIVE_COMP intValue
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`<main_parameter>`|intValue, contains the ID of the componed to be set active.|

# Returns:  

none

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

Sets one component after the other to active and after each displays an infobox.  
```adoscript
{% raw %}

FOR i from:1 to:6
{
  CC "Application" SET_ACTIVE_COMP (i)
  CC "AdoScript" INFOBOX ("Active component set to " + STR i)
}

{% endraw %}
```
{: .line-numbers}


