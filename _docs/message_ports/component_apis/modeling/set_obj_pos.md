---
layout: commandcall
category: CommandCall
title: "SET_OBJ_POS"
tags: 1.3 1.5
---

SET_OBJ_POS sets the position of a modeling object.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_OBJ_POS objid:id x:measureValue y:measureValue .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`x`|measureValue|
|`y`|measureValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_SELECTED
FOR objid in:(objids) {
    CC "Core" GET_CLASS_ID objid:(VAL objid)
    IF (NOT isrel) {
        # get position
        CC "Core" GET_ATTR_ID classid:(classid) attrname:"Position"
        CC "Core" GET_ATTR_VAL objid:(VAL objid) attrid:(attrid)
        LEO parse:(val) get-tmm-value:x:"x" get-tmm-value:y:"y"
        # increment x coordinate and set new position
        SET x:(x + 1cm)
        CC "Modeling" SET_OBJ_POS objid:(VAL objid) x:(x) y:(y)
    }
}

{% endraw %}
```
{: .line-numbers}


