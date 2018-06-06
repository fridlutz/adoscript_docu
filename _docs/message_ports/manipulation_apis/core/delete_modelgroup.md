---
layout: commandcall
category: CommandCall
title: "DELETE_MODELGROUP"
tags: 1.3 1.5
---

DELETE_MODELGROUP deletes an existing modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_MODELGROUP mgroupid:intValue

#--> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

mgroupid, id of the modelgroup that should be deleted

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:



# See Also:  

[CREATE_MODELGROUP](create_modelgroup.html "CREATE_MODELGROUP")  


Example 1:

```adoscript
{% raw %}

# let the user select a parent modelgroup
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel

# within the selected modelgroup, create a new modelgroup
CC "Core" DELETE_MODELGROUP mgroupid:(VAL token(mgroupids,0," "))

IF (ecode != 0)
{
   CC "AdoScript" INFOBOX "Error!\nModelgroup could not be deleted. Are there still modelreferences in the modelgroup?"
}

{% endraw %}
```
{: .line-numbers}

