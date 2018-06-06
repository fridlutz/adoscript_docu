---
layout: commandcall
category: CommandCall
title: "GET_USER_ID"
tags: 1.3 1.5
---

GET_USER_ID returns the ID of an ADOxx user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_USER_ID user:strValue .


# --> RESULT ecode:intValue userid:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the user which id should be returned|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`userid`|intValue, The ID of the specified ADOxx user.|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_USER_ID user:"Travolta"
IF (ecode = 0) {
    CC "AdoScript" INFOBOX (STR userid)
} ELSE {
    CC "AdoScript" ERRORBOX "User ID could not be retreived!"
}

{% endraw %}
```
{: .line-numbers}

