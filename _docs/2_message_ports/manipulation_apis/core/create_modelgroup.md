---
layout: commandcall
category: CommandCall
title: "CREATE_MODELGROUP"
tags: 1.3 1.5
---

CREATE_MODELGROUP creates a new modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_MODELGROUP supermgroupid:intValue mgroupname:strValue 

#--> RESULT ecode:intValue mgroupid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`supermgroupid`|intValue, id of the parent modelgroup (the modelgroup in which the new modelgroup should be created)|
|`mgroupname`|strValue, the name of the new modelgroup|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`mgroupid`|intValue, the ID of the newly created modelgroup.|

# Remarks:



# See Also:  

[DELETE_MODELGROUP](delete_modelgroup.html "DELETE_MODELGROUP")  


Example 1:

Create a new modelgroup  
```adoscript
{% raw %}

# let the user select a parent modelgroup
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel

# within the selected modelgroup, create a new modelgroup
CC "Core" CREATE_MODELGROUP supermgroupid:(VAL token(mgroupids,0," "))
                            mgroupname:"MyModelgroup"

IF (ecode != 0)
{
   CC "AdoScript" INFOBOX "Error!\nModelgroup could not be created. Was the name you entered unique?"
}

{% endraw %}
```
{: .line-numbers}

