---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_ID"
tags: 1.3 1.5
---

GET_MODELGROUP_ID determines the ID of a model group which is specified as path.

# Syntax:  

```adoscript
{% raw %}
CC Core" GET_MODELGROUP_ID	 mgroupname:strValue sep:strValue

#--> RESULT ecode:intValue mgroupid:id .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupname`|strValue, specifies the full modelgroup path.|
|`sep`|strValue, specifies the character with which the single model group names of the path are separated. A good value for sep is "\t" (TAB character), as this character cannot occur in a model group name. The parameter sep must always be specified, even if you try to resolve a top model group.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`mgroupid`|intValue, contains the ID of the modelgroup|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# this tries to resolve the ID of the modelgroup
# "Modelle --> Bereiche --> Entwicklung --> Philip"
CC "Core" GET_MODELGROUP_ID
      mgroupname:"Modelle\tBereiche\tEntwicklung\tPhilip" sep:"\t"

# this tries to resolve the ID of the root modelgroup 'Modelle'
CC "Core" GET_MODELGROUP_ID mgroupname:"Modelle" sep:"\t"

{% endraw %}
```
{: .line-numbers}

