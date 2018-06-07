---
layout: commandcall
category: CommandCall
title: "GET_APP_INFO"
tags: 1.3 1.5
---

GET_APP_INFO returns information about the current ADOxx application.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_APP_INFO	

#--> RESULT app:strValue ws: 0|1 . 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`app`|strValue, is either "bpmtk" for areena.exe or awssvr.exe or "admintk" for aadma.exe|
|`ws`|0|1, is 1 when running in web service mode (awssvr.exe)|

# Remarks:



# See Also:  



Example 1:

Executing code only in web service mode.  
```adoscript
{% raw %}

CC "Application" GET_APP_INFO
IF (ws) {'
    # web service specific code
}

{% endraw %}
```
{: .line-numbers}


