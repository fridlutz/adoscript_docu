---
layout: commandcall
category: CommandCall
title: "USERSETTINGS_SET_TO_DEFAULT"
tags: 1.3 1.5
---

USERSETTINGS_SET_TO_DEFAULT resets these settings to the default values stored in the library.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" USERSETTINGS_SET_TO_DEFAULT
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

[USERSETTINGS_SAVE_TO_DB](usersettings_save_to_db.html "USERSETTINGS_SAVE_TO_DB")  
[USERSETTINGS_RESTORE_FROM_DB](usersettings_restore_from_db.html "USERSETTINGS_RESTORE_FROM_DB")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" USERSETTINGS_SET_TO_DEFAULT

{% endraw %}
```
{: .line-numbers}

