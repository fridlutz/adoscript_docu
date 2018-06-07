---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODEL_VERSIONS_OF_THREAD"
tags: 1.3 1.5
---

GET_ALL_MODEL_VERSIONS_OF_THREAD returns a list of all model versions of specified model thread.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_MODEL_VERSIONS_OF_THREAD	modelthreadid:intValue

#-->RESULT ecode:intValue modelversionids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelthreadid`|intValue, the ID of the model thread|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelversionids`|strValue, contains a list with all model versions.|

# Remarks:



# See Also:  

[GET_MODEL_THREAD_OF_VERSION](get_model_thread_of_version.html "GET_MODEL_THREAD_OF_VERSION")  


Example:

