---
layout: commandcall
category: CommandCall
title: "SET_MODELGROUP_NAME"
tags: 1.3 1.5
---

SET_MODELGROUP_NAME renames an existing modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_MODELGROUP_NAME mgroupid:intValue mgroupname:strValue

#--> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid`|intValue, the ID of the model group|
|`mgroupname`|strValue, the new name to be set|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:



# See Also:  



Example 1:

Getting the name of a modelgroup  
```adoscript
{% raw %}

# let the user select a modelgroup
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel

# get the name of the modelgroup
CC "Core" SET_MODELGROUP_NAME mgroupid:(VAL token(mgroupids,0," "))
                              mgroupname:"New Name"

IF (ecode != 0)
{
   CC "AdoScript" INFOBOX ("Renaming failed: " + STR ecode)
}

{% endraw %}
```
{: .line-numbers}

