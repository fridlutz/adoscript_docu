---
layout: commandcall
category: CommandCall
title: "GET_VIS_ATTR_ID"
tags: 1.3 1.5
---

GET_VIS_ATTR_ID returns the attribute ID of a visible attribute of a modeling object or connector.

# Syntax:  

```adoscript
{% raw %}
GetVisAttrID :	GET_VIS_ATTR_ID modelid:intValue objid:intValue index:intValue .


# --> RESULT attrid:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|
index - intValue, the index is between 0 and (count - 1), where count has been returned by GET_VIS_ATTR_COUNT.

# Returns:  

|`attrid`|intValue|

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


