---
layout: commandcall
category: CommandCall
title: "HTTP_REQUEST"
tags: 1.3 1.5
---

HTTP_REQUEST sends an HTTP request and gets the related response.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" HTTP_REQUEST	strValue 	[ verb:strValue ] [ binary[:boolValue] ]
									[ timeouts:strValue ] [ retry:intValue ] [ proxy:strValue ]
									[ proxyuser:strValue ] [ proxypw:strValue ] .

# --> RESULT ecode:intValue response:strValue 
			 header:strValue charset:strValue host:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the target URL|
|`verb`|strValue, specifies the HTTP request type and must be either "GET" (which is the default) or "POST".|
|`binary`|boolValue, if specified, the response will be left in binary format|
|`timeouts`|strValue, contains 4 semicolon-separated integer values, specifying the resolve timeout, the connect timeout, the send timeout and the receive timeout in milliseconds. The default value is "0;60000;30000;30000". Default values are also applied when the passed string is wrong or incomplete.|
|`retry`|intValue, sets the maximum number of send tries, where 1 is the default.|
|`proxy`|strValue, the proxy server|
|`proxyuser`|strValue, the prody user|
|`proxypw`|strValue , the password for the proxy user|

# Returns:  

|`ecode`|intValue|
|`response`|strValue, contains the actual file content. This could be simple text or HTML, but also binary data like the content of a graphics file, which can be saved to a file.|
|`header`|strValue, contains the HTTP response header|
|`charset`|strValue, the name of the used character set|
|`host`|strValue, the addressed host name|

# Remarks:

The web address and all return values are encoded in UTF-8. Only the response can alternatively be left in binary format by specifying the binary option.

The optional proxy parameters specify a proxy server (proxy), a proxy user (proxyuser) and a password of the proxy user (proxypw) as UTF-8 encoded strings.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" HTTP_REQUEST "http://www.adoxx.org"
CC "AdoScript" VIEWBOX text:(response)

{% endraw %}
```
{: .line-numbers}


Example 2:

```adoscript
{% raw %}

SET url:"http://www.pohlw.de/vor_ort/emigration_whs/bauernreg_grk.pdf"
CC "AdoScript" HTTP_REQUEST (url) binary
CC "AdoScript" FWRITE file:"d:\\test.pdf" text:(response) binary

{% endraw %}
```
{: .line-numbers}
