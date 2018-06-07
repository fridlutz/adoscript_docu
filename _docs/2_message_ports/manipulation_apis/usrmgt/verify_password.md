---
layout: commandcall
category: CommandCall
title: "VERIFY_PASSWORD"
tags: 1.3 1.5
---

VERIFY_PASSWORD passes and verifies a users log on name and password, returning a user id, library type and name.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" VERIFY_PASSWORD user:strValue password:strValue singlesignon:intValue

# --> RESULT ecode:intValue userid:intValue libname:strValue libtype:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, is the login name for a user.|
|`password`|strValue, is the login password for the user.|
|`singlesignon`|intValue, has a value of 0 for a non single sign on user, and 1 for a single sign on user.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`userid`|intValue, ID of the user|
|`libname`|strValue, the name of the library|
|`libtype`|strValue, the type of the library|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" VERIFY_PASSWORD
        user:"adouser1" password:"adouser1" singlesignon:0
{% endraw %}
```
{: .line-numbers}

