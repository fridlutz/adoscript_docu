---
layout: commandcall
category: CommandCall
title: "GET_ACCESS_MODE"
tags: 1.3 1.5
---

GET_ACCESS_MODE returns the current user's acces mode of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ACCESS_MODE modelid:id [ with-username ] [ with-permission ] .

#-->RESULT ecode:intValue access:strValue isloaded:1|0
			[ username:strValue ] [ permission:strValue ] .
			
AccessMode : "read" | "write" .
Permission : "none" | "read" | "write" .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the model is specified by its ID.|
|`with-username`|modifier, if specified, the result is extended by a return variable username, which holds the name of the user who currently has locked the model (i.e. loaded the model with write access). If the model is not locked by any user this value is an empty string.|
|`with-permission`|if specified, the result is extended by a return variable permission, which holds the maximum access mode with which the model could be loaded. This is determined by the maximumn model group access on the model groups which contain the model.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`access`|strValue, "read" if the user is only permitted to read the model status or "write" if the user may also change it.|
|`isloaded`|1|0, 1 if the model is loaded, otherwise it is 0. This is helpful to determine, whether you queried the access mode on a loaded model or not, since access is always "read" if a model is not loaded.|
|`username`|strValue, the name of the user who currently has locked the model|
|`permission`|strValue, the maximum access mode with which the model could be loaded.|

# Remarks:



# See Also:  



Example 1:

Show detailed access mode info of a selected model  
```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX
IF (endbutton = "ok") {
    SET modelid:(VAL modelids)
    CC "Core" GET_ACCESS_MODE modelid:(modelid) with-username with-permission
    SET s:"Access mode: %1\nIs loaded: %2\nUser: %3\nPermission: %4"
    SET s:(replace(s, "%1", mstr(access)))
    SET s:(replace(s, "%2", STR isloaded))
    SET s:(replace(s, "%3", mstr(username)))
    SET s:(replace(s, "%4", mstr(permission)))
    CC "AdoScript" INFOBOX (s)
}

{% endraw %}
```
{: .line-numbers}

