---
layout: commandcall
category: CommandCall
title: "GET_DBMS"
tags: 1.3 1.5
---

GET_DBMS returns a string which identifies the currently used database system.

# Syntax:  

```adoscript
{% raw %}
CC "DB" GET_DBMS

#--> RESULT dbms: stringValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`dbms`|stringValue, one of the following values: "db2", "oracle", "informix", "sqlserver" or "none"; "none" indicates that no DBMS is active. In a normal environment this should actually never be returned.|

# Remarks:



# See Also:  



Example 1:  
Get the currently active database system

```adoscript
{% raw %}

CC "DB" GET_DBMS
CC "AdoScript" INFOBOX ("You are currently using: " + dbms)

{% endraw %}
```
{: .line-numbers}

