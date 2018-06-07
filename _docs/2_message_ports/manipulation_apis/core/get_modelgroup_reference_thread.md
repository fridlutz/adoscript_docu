---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_REFERENCE_THREAD"
tags: 1.3 1.5
---

GET_MODELGROUP_REFERENCE_THREAD returns the id of the modelthread to which the modelgroup reference points.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_REFERENCE_THREAD refid:intValue

#--> RESULT ecode:intValue  threadid:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`refid`|intValue, the id of the modelgroup reference|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`threadid`|intValue, the id of the referenced model thread.|

# Remarks:



# See Also:  



Example 1:

Creating a new modelgroup reference  
```adoscript
{% raw %}

# let the user select a modelgroup
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel
SET mgroup:(VAL token(mgroupids,0," "))

# let the user select a modelthread
CC "CoreUI" MODEL_SELECT_BOX threads
SET mthread:(VAL token (threadids,0," "))

# create a new reference
CC "Core" CREATE_MGROUP_REFERENCE mgroupid:(mgroup) threadid:(mthread)
SET mref:(refid)

CC "Core" GET_MODELGROUP_REFERENCE_THREAD refid:(mref)

CC "AdoScript" INFOBOX ("Thread: " + STR threadid)

{% endraw %}
```
{: .line-numbers}

