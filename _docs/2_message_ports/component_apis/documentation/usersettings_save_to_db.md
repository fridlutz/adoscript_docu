---
layout: commandcall
category: CommandCall
title: "USERSETTINGS_SAVE_TO_DB"
tags: 1.3 1.5
---

USERSETTINGS_SAVE_TO_DB saves these settings in the user specific part of the library.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" USERSETTINGS_SAVE_TO_DB
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

If an user changes something in the documentation settings dialog, these changes will be stored in an user specific entry in the db.

# See Also:  

[USERSETTINGS_RESTORE_FROM_DB](usersettings_restore_from_db.html "USERSETTINGS_RESTORE_FROM_DB")  
[USERSETTINGS_SET_TO_DEFAULT](usersettings_set_to_default.html "USERSETTINGS_SET_TO_DEFAULT")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" USERSETTINGS_SAVE_TO_DB

{% endraw %}
```
{: .line-numbers}

