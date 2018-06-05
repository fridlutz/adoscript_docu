---
layout: commandcall
category: CommandCall
title: "GET_MODEL_THREAD_OF_VERSION"
tags: 1.3 1.5
---

GET_MODEL_THREAD_OF_VERSION returns the core id of the model thread of specified model version.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_THREAD_OF_VERSION	modelversionid:intValue

#--> RESULT ecode:intValue modelthreadid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelversionid`|intValue, the ID of the model version|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelthreadid`|intValue, the core id of the thread of specified model version.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_ALL_MODEL_VERSIONS
SET first:(token(modelversionids, 0, " "))
CC "Core" GET_MODEL_THREAD_OF_VERSION modelversionid:(VAL first)
IF (ecode) {
    CC "AdoScript" ERRORBOX ("Error: " + STR ecode)
} ELSE {
    CC "AdoScript" INFOBOX ("Model thread ID: " + STR modelthreadid)
}

{% endraw %}
```
{: .line-numbers}

