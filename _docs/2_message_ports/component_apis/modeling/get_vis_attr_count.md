---
layout: commandcall
category: CommandCall
title: "GET_VIS_ATTR_COUNT"
tags: 1.3 1.5
---

GET_VIS_ATTR_COUNT returns the number of attributes of a modeling object or connector visible in the graphical representation.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_VIS_ATTR_COUNT modelid:intValue objid:intValue .


# --> RESULT count:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`objid`|intValue|

# Returns:  

|`count`|intValue|


# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_SELECTED
IF (ecode = 0) {
  SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:mid
  SET modelid:(VAL mid)
  FOR objid in:(objids) {
    CC "Modeling" debug GET_VIS_ATTR_COUNT modelid:(modelid) objid:(VAL objid)
    FOR index from:0 to:(count - 1) {
      CC "Modeling" debug GET_VIS_ATTR_ID modelid:(modelid) objid:(VAL objid) index:(index)
      CC "Modeling" debug GET_VIS_ATTR_BOUNDS modelid:(modelid) objid:(VAL objid) index:(index)
    }
  }
}

{% endraw %}
```
{: .line-numbers}


