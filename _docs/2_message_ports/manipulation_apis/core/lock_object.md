---
layout: commandcall
category: CommandCall
title: "LOCK_OBJECT"
tags: 1.3 1.5
---

LOCK_OBJECT locks the an object in the database.

# Syntax:  

```adoscript
{% raw %}
CC "Core" LOCK_OBJECT objid:id [ type:LockType ] .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
LockType :	"write" | "shared" .


#-->RESULT ecode:intValue already_locked:boolValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`type`|LockType|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`already_locked`|boolValue|

# Remarks:

The ID of the object is specified with objid.  
Two different types of locks can be set: type:"write", which is the default, means exclusive write access. Shared access (type:"shared") is used to implement concurrent editing of one model by multiple users. (This will soon be be documented extra.)  
If the object is already locked the value of already_locked becomes 1, otherwise 0.  
If you use this function make sure that you call the UNLOCK_OBJECT function with the same ID! The given ID can be anything - even a metamodel ID so be VERY careful!

# See Also:  



Example:

