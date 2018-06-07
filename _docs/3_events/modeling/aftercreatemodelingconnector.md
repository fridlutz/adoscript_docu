---
layout: event
category: Event
title: "AfterCreateModelingConnector"
tags: 1.3 1.5
---

This event is triggered by the graphical model editor after a new connector has been created.  

# Parameters:  

modelid	- intValue, ID of the concerned model.
|`objid`|intValue, ID of the new connector.|
|`classid`|intValue, ID of the new connector's relation class.|
|`fromobjid`|intValue, ID of the new connector's "from" object.|
|`toobjid`|intValue, ID of the new connector's "to" object.|
|`origin`|intValue; 0 if the new connector has been modeled by user or 1 if the connector has been pasted (copy-paste or cut-paste).|

Exit value:



# Remarks:  



# See Also:  



Example:

```adoscript
{% raw %}

ON_EVENT "AfterCreateModelingNode" {
    CC "AdoScript" FWRITE
        file:"d:\\event.log"
        text:("AfterCreateModelingNode"
                " modelid:" + STR modelid + " objid:" + STR objid +
                " classid:" + STR classid + " origin:" + STR origin + "\n")
}


ON_EVENT "AfterCreateModelingConnector" {
    CC "AdoScript" FWRITE
        file:"d:\\event.log"
        text:("AfterCreateModelingConnector" +
                " modelid:" + STR modelid + " objid:" + STR objid +
                " classid:" + STR classid + " fromobjid:" + STR fromobjid +
                " toobjid:" + STR toobjid + " origin:" + STR origin + "\n")
}

{% endraw %}
```
{: .line-numbers}

