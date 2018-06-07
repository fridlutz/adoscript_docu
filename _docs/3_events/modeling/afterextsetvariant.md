---
layout: event
category: Event
title: "AfterExtSetVariant"
tags: 1.3 1.5
---

This event is triggered after a variant has been activated via the modeling component. Via the modeling component means that together with the variant activation a related layout algorithm may have been executed.  

# Parameters:  

|`modelid`|intValue, ID of the changed model.|
|`newvariant`|strValue, name of the new variant.|
|`oldvariant`|strValue, name of the old variant.|
|`layalgname`|strValue, language independent name of the executed layout algorithm.|
|`layalguiname`|strValue, language independent name of the executed layout algorithm.|

Exit value:



# Remarks:  

If the variant has been activated without automatically execute a layout algorithm (e.g. because the variant does already contain some object positions), the variables layalgname and layalguiname are set to empty strings.  

# See Also:  



Example:

```adoscript
{% raw %}

ON_EVENT "AfterExtSetVariant" {
    SET s:("Variant " + mstr(newvariant) + " has been activated.\n"
         + "Model ID: " + STR modelid + "\n"
         + "Old variant: " + mstr(oldvariant) + "\n"
         + "Layout algorithm: " + mstr(layalguiname))
    CC "AdoScript" INFOBOX (s)
}

{% endraw %}
```
{: .line-numbers}

