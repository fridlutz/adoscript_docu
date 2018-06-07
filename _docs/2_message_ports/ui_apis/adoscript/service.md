---
layout: commandcall
category: CommandCall
title: "SERVICE"
tags: 1.3 1.5
---

Starts or stopps the ADOxx Web Service server.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" SERVICE	Start | Stop

Start :		start 	[ port:intValue ] [ backlog:intValue ]
					[ logformat:"short" | "long" ] [ output: statusbar | textfield ] .

Stop :		stop .

# -->RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`start`|modifier, starts the ADOxx Web Service server.|
|`port`|intValue, port at which the ADOxx Web Service server receives requests. Default is 80.|
|`backlog`|intValue, max queue size for requests. Default is 100.|
|`logformat`|"short" | "long"|
|`output`|statusbar | textfield, specifies where the status messages of the ADOxx Web Service server are put out. **statusbar** (default) means the  messages are shown in the status bar and **textfield** means that messages are appended to a textfield. As this reduces the server performance (in relation to statusbar mode), this mode should just be used when really needed.|
|`stop`|modifier, ends the ADOxx Web Service server.|

# Returns:  

|`ecode`|intValue|

# Remarks:



# See Also:  



Example:



