---
layout: commandcall
category: CommandCall
title: "SWITCH_USER_CONTEXT"
tags: 1.3 1.5
---

SWITCH_USER_CONTEXT activates a special user context, which means that the application (temporarily) behaves as if another user than the login user is the active one.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" SWITCH_USER_CONTEXT userid:intValue | default 

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userid`|intValue, specifies an existing user|
|`default`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

To switch back to the original status the command has to be called with default.

While the application is running in a special user context, the special user is not really logged in with the running application instance, which means that the a user context can be used for several application instances at the same time, while this is not allowed for login users.

The switching to a special user context and the back-switching must happen in the same running script. When a script terminates in a special user context, the user context is reset automatically. (However, scripts should not rely on that behavior.)

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_USER_ID user:"Özil"
CC "UserMgt" SWITCH_USER_CONTEXT userid:(userid)
# ...
CC "UserMgt" SWITCH_USER_CONTEXT default

{% endraw %}
```
{: .line-numbers}

