---
layout: event
category: Event
title: "BeforeExtSetVariant"
tags: 1.3 1.5
---

This event is triggered before a variant is being activated via the modeling component. Via the modeling component means that together with the variant activation a related layout algorithm may be executed.  

# Parameters:  

|`modelid`|intValue, ID of the affected model.|
|`newvariant`|strValue, name of the new variant.|
|`oldvariant`|strValue, name of the old variant.|
|`layalgname`|strValue, language independent name of the layout algorithm which will be executed.|
|`layalguiname`|strValue, language independent name of the layout algorithm which will be executed.|

Exit values:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with runtime error (not recommended).|

# Remarks:  

If the variant will be activated without automatically executing a layout algorithm (e.g. because the variant does already contain some object positions), the variables layalgname and layalguiname are set to empty strings.

It is possible to forbid to switch to a variant, e.g. in dependence on a certain model status. This can be achieved by exiting the variant handler with a nonzero value. If the exit value is -1 (which is by now the only recommended nonzero value), an error box should be shown by the event handler before exiting, so the user is informed why switching to the new variant failed.  

# See Also:  



Example:

```adoscript
{% raw %}

ON_EVENT "BeforeExtSetVariant" {
    SET s:("Variant " + mstr(newvariant) + " has been activated.\n"
         + "Model ID: " + STR modelid + "\n"
         + "Old variant: " + mstr(oldvariant) + "\n"
         + "Layout algorithm: " + mstr(layalguiname))
    CC "AdoScript" INFOBOX (s)
    IF (newvariant = "Dummy") {
        CC "AdoScript" ERRORBOX "The dummy variant cannot be used."
        EXIT -1
    }
}

{% endraw %}
```
{: .line-numbers}

