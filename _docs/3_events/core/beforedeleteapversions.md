---
layout: event
category: Event
title: "BeforeDeleteAPVersions"
tags: 1.3 1.5
---

This event is triggered before attribute profiles are deleted. If more than one ID is passed, this means that a couple of attribute profiles is going to be deleted at once.  

# Parameters:  

|`apversionids`|strValue, ID container of attribute profile versions which are going to be deleted.|

Exit value:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with error.|
|`greater than 0`|Abort with core error code.|

# Remarks:  

If the event handler is exited with a nonzero value, deleting the attribute profiles will not be performed. If the exit value is -1, the deletion is aborted without an error. If the exit value is -2, the deletion is aborted with an error.

The difference between without and with error is that if the deletion has been called via the UI just in the second case an error message appears. The without error case is useful if an error message is already displayed by the event handler. If the deletion has been called via AdoScript, the difference is that different core error codes are returned at the delete command.  

# See Also:  



Example:

The following event handler makes it impossible to delete more than one attribute profile at once  
```adoscript
{% raw %}

ON_EVENT "BeforeDeleteAPVersions" {
    IF (tokcnt(appversionids) > 1) {
        SET err:"Don't try to delete more than one AP at once! :-)"
        CC "AdoScript" ERRORBOX (err)
        EXIT -1  # abort without error
    }
}

{% endraw %}
```
{: .line-numbers}

