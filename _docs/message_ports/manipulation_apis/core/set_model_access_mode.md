---
layout: commandcall
category: CommandCall
title: "SET_MODEL_ACCESS_MODE"
tags: 1.3 1.5
---

SET_MODEL_ACCESS_MODE can only be used in the OpenModel AdoScript-Event.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_MODEL_ACCESS_MODE modelversionid:intValue read-access:[0|1]

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelversionid`|intValue, the ID of the model version|
|`read-access`|1|0|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

If this command is called with "read-access:1" the model is anyway loaded with readonly access! It can be used to implement a Checkin/Checkout mechanism in ADOxx.

The AdoScript events must be customized into the library attribute "External Coupling".


# See Also:  



Example 1:

```adoscript
{% raw %}

ON_EVENT "OpenModel"
{
  # queries the active user
  CC "Application" GET_USER

  if (user = "Readonly")
  {
    # only readonly!
    CC "Core" SET_MODEL_ACCESS_MODE modelversionid:(modelid) read-access:1
  }
}

{% endraw %}
```
{: .line-numbers}

