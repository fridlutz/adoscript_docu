---
layout: commandcall
category: CommandCall
title: "MOVE_MODELGROUP_REFERENCE"
tags: 1.3 1.5
---

MOVE_MODELGROUP_REFERENCE moves the reference specified by refid to the modelgroup specified by targetmgroupid.  


# Syntax:  

```adoscript
{% raw %}
CC "Core" MOVE_MODELGROUP_REFERENCE refid:intValue targetmgroupid:intValue 

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`refid`|intValue, the ID of the reference|
|`targetmgroupid`|intValue, the ID of the target model group|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get all top level groups
CC "Core" GET_MGROUP_SUBGROUPS

# if there are less than 2 issue an error
IF (tokcnt (submgroupids, " ") < 2)
{
  CC "AdoScript" INFOBOX ("There must be at least 2 root groups!\n" +
                          " Now there are " + STR tokcnt (submgroupids, " ") + " root groups")
  EXIT
}

# set source and target modelgroup ID
SET mg1:(VAL token (submgroupids, 0, " "))
SET mg2:(VAL token (submgroupids, 1, " "))

# get all references of first modelgroup
CC "Core" GET_MGROUP_REFERENCES mgroupid:(mg1)

# if there is no reference -> error
IF (refids = "")
{
  CC "AdoScript" INFOBOX ("The first modelgroup does not contain any reference!")
  EXIT
}

# get first reference
SET srcrefid:(VAL token (refids, 0, " "))

# and copy to second group
CC "Core" COPY_MODELGROUP_REFERENCE refid:(srcrefid) targetmgroupid:(mg2)

# get second reference
SET srcrefid:(VAL token (refids, 1, " "))

# and move to second group
CC "Core" MOVE_MODELGROUP_REFERENCE refid:(srcrefid) targetmgroupid:(mg2)

{% endraw %}
```
{: .line-numbers}

