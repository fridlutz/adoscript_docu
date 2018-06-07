---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_PARENT"
tags: 1.3 1.5
---

GET_MODELGROUP_PARENT returns the id of the parent modelgroup of one modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_PARENT mgroupid:intValue

#--> RESULT ecode:intValue parentmgroupid:id 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid`|intValue, specifies the ID of the modelgroup|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`parentmgroupid`|intValue, id of the parent modelgroup (the modelgroup that contains the selected modelgroup.|

# Remarks:



# See Also:  



Example 1:

Getting the parent modelgroup  
```adoscript
{% raw %}

# let the user select a modelgroup
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel

# get the name of the parent modelgroup
CC "Core" GET_MODELGROUP_PARENT mgroupid:(VAL token(mgroupids,0," "))

IF (ecode = 0)
{
   CC "Core" GET_MODELGROUP_NAME mgroupid:(parentmgroupid)
}

# display the name
IF (ecode = 0)
{
   IF (mgroupname = "root")
   {
      CC "AdoScript" INFOBOX "You selected a top-level modelgroup!"
   }
   ELSE
   {
      CC "AdoScript" INFOBOX ("The selected the modelgroup is within " + mgroupname)
   }
}

{% endraw %}
```
{: .line-numbers}

