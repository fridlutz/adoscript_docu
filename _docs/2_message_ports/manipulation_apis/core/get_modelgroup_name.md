---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_NAME"
tags: 1.3 1.5
---

GET_MODELGROUP_NAME returns the name of a modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_NAME mgroupid:intValue

#--> RESULT ecode:intValue  mgroupname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid `|intValue, specifies the ID of the modelgroup|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`mgroupname`|strValue, contains the name of the modelgroup|

# Remarks:



# See Also:  



Example 1:

Getting the name of a modelgroup  
```adoscript
{% raw %}

# let the user select a modelgroup
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel

# get the name of the modelgroup
CC "Core" GET_MODELGROUP_NAME mgroupid:(VAL token(mgroupids,0," "))

IF (ecode = 0)
{
   CC "AdoScript" INFOBOX ("You selected the modelgroup: "+mgroupname)
}

{% endraw %}
```
{: .line-numbers}

