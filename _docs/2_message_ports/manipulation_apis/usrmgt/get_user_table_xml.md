---
layout: commandcall
category: CommandCall
title: "GET_USER_TABLE_XML"
tags: 1.3 1.5
---

GET_USER_TABLE_XML generates an XML string containing information about all existing users and user groups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_USER_TABLE_XML

# --> RESULT xml:strValue ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue|

# Remarks:

The resulting XML string (xml) has the following structure:  
```adoscript
{% raw %}
<root>
<usergroups>
{ <usergroup ... /> }
</usergroups>
<users>
{ <user ... /> }
</users>
</root>
{% endraw %}
```
{: .line-numbers}

A usergroup tag has following attributes  
id - ID of the current user group  
type - either "system" (system user group) or "internal" (ADOxx user group)  
name - user group name

A user tag has following attributes  
id - ID of the current user  
type - either "system" (system user) or "internal" (ADOxx user)  
domain - domain name of the current user  
name - user name  
applibid - ID of the application library related to the current user  
comment - user specific information  
usergroups - related user group IDs, separated by ";" (semicolon)

# See Also:  



Example:

