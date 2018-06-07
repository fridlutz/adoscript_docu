---
layout: event
category: Event
title: "AfterCreateModelingNode"
tags: 1.3 1.5
---

This event is triggered by the graphical model editor after a new instance has been created.  

# Parameters:  

|`modelid`|intValue, the ID of the concerned model.|
|`objid`|intValue, the ID of the new object.|
|`classid	`|intValue, the  of the new object's class.|
|`origin`|intValue; 0 if the new object has been modeled by user; 1 if the object has been pasted (copy-paste or cut-paste); 2 if the object has been created by undoing a previous delete or cut action.|

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

