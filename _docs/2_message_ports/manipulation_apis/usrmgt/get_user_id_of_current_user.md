---
layout: commandcall
category: CommandCall
title: "GET_USER_ID_OF_CURRENT_USER"
tags: 1.3 1.5
---

GET_USER_ID_OF_CURRENT_USER returns the ID of the current ADOxx user.  
This command works both for system and normal users.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_USER_ID_OF_CURRENT_USER

# --> RESULT ecode:intValue userid:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`userid`|intValue, The ID of the current ADOxx user.|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example:

