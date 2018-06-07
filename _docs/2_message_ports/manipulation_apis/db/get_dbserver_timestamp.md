---
layout: commandcall
category: CommandCall
title: "GET_DBSERVER_TIMESTAMP"
tags: 1.3 1.5
---

GET_DBSERVER_TIMESTAMP returns the current server date and time as a string. The returned timestamp depends on the time settings on the database server.

# Syntax:  

```adoscript
{% raw %}
CC "DB" GET_DBSERVER_TIMESTAMP	

#--> RESULT ecode:intValue errtext:strValue timestamp:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  



# Remarks:

ecode - intValue, Contains the error code or is 0 in case of success.  
errtext - strValue, contains a textual representation of the ecode.  
timestamp - strValue; has THE format "yyyy-mm-dd,hh:MM:ss".

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "DB" GET_DBSERVER_TIMESTAMP
CC "AdoScript" INFOBOX ("The current server timestamp is: " + timestamp)

{% endraw %}
```
{: .line-numbers}

