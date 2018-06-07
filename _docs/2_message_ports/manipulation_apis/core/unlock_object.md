---
layout: commandcall
category: CommandCall
title: "UNLOCK_OBJECT"
tags: 1.3 1.5
---

UNLOCK_OBJECT removes a DB lock for the given ID (objid) .

# Syntax:  

```adoscript
{% raw %}
CC "Core" UNLOCK_OBJECT objid:intValue . 


#-->RESULT ecode:intValue not_locked:[0|1]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`not_locked`|[0|1]|

# Remarks:

Call UNLOCK_OBJECT for each object you locked with LOCK_OBJECT.  
If you forget to remove a lock it is NOT automatically unlocked! The ID must be exactly the same as specified in LOCK_OBJECT.  
If the given ID is not locked (anymore) in the DB, not_locked is 1. If unlocking was successful eCode must be 0 and not_locked must also be 0!

# See Also:  



Example:

