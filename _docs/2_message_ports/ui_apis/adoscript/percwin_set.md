---
layout: commandcall
category: CommandCall
title: "PERCWIN_SET"
tags: 1.3 1.5
---

PERCWIN_SET sets a new percentage value and/or a new message text.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" PERCWIN_SET	[ percentage:realValue] [ text:strValue]
							[ percentage2:realValue] [ text2:strValue]

 # --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`percentage`|realValue, sets the current percentage value of the progress bar|
|`text`|strValue, sets a message text (e.g. about the current action)|
|`percentage2`|realValue, sets the percentage value of the second progress bar|
|`text2`|strValue, sets a message text for the second percentage bar|

# Returns:  

|`ecode`|intValue|

# Remarks:



# See Also:  

[PERCWIN_CREATE](percwin_create.html "PERCWIN_CREATE")  
[PERCWIN_IS_CANCELED](percwin_is_canceled.html "PERCWIN_IS_CANCELED")  
[PERCWIN_DESTROY](percwin_destroy.html "PERCWIN_DESTROY")  


Example 1:

```adoscript
{% raw %}

SET t1:(getTickCount())
CC "AdoScript" PERCWIN_CREATE title:"Performance-Test"
SET count:20000
FOR i from:1 to:(count) {
    SET text:("This is a test:\n"
            + STR INT (random()**1000) + " "
            + STR INT (random()**1000) + " "
            + STR INT (random()**1000))
    CC "AdoScript" PERCWIN_SET percentage:(100 ** i / count) text:(text)
}
CC "AdoScript" PERCWIN_DESTROY
SET t2:(getTickCount())
SET sec:((t2 - t1) ** 0.001)
CC "AdoScript" INFOBOX ("The script took " + STR sec + " seconds.")

{% endraw %}
```
{: .line-numbers}

