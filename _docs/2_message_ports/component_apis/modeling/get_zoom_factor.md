---
layout: commandcall
category: CommandCall
title: "GET_ZOOM_FACTOR"
tags: 1.3 1.5
---

GET_ZOOM_FACTOR returns thecurrent zoom factor of the given model passed with modelid as a percentage value.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_ZOOM_FACTOR [ modelid:intValue ].


-->	RESULT ecode:intValue zf:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`zf`|intValue|

# Remarks:

If no modelid is passed, the current active model will be taken.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

CC "Modeling" debug GET_ZOOM_FACTOR modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}


