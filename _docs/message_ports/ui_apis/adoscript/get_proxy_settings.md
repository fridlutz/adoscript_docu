---
layout: commandcall
category: CommandCall
title: "GET_PROXY_SETTINGS"
tags: 1.3 1.5
---

GET_PROXY_SETTINGS gets the Internet Explorer proxy settings for the current user.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" GET_PROXY_SETTINGS

# --> RESULT ecode:intValue proxy:strValue  .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, 0 if the call succeeds or 1 otherwise.|
|`proxy`|strValue, contains the defined settings with semicolon (';') as separator.|

# Remarks:

Each setting will have the type/name of the setting and a value in the form &lt;Type/Name&gt;=&lt;Value&gt;  . E.g. the variable proxy might contain something like   http=10.0.2.8:8000;https=10.0.2.8:8000  . So if you are interested in the settings of a certain type, search within the according token for the '=' sign (using separator ';').

If there is only one general setting (due to having the same proxy set for all protocols), the returned string will not contain any '=' character, e.g. 10.0.2.8:8000

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" GET_PROXY_SETTINGS
FOR n from:0 to:(tokcnt(proxy, ";")-1)
{
  SET s:(token (proxy, n, ";"))
  CC "AdoScript" INFOBOX ("Setting for " + token(s, 0, "=") + " is: " + token(s, 1, "="))
}

{% endraw %}
```
{: .line-numbers}

