---
layout: commandcall
category: CommandCall
title: "XML_CLOSE"
tags: 1.3 1.5
---

XML_CLOSE closes a file that is currently imported or exported.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_CLOSE read | write
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`read`|modifier, closes the current intput file (default).|
|`write`|modifier, closes the current output file.|


# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Documentation" XML_OPEN "outputfile.xml" write
CC "Documentation" XML_OPEN "inputfile.xml"
CC "Documentation" XML_CLOSE write
# now the file "inputfile.xml" is opened, the file "outputfile.xml" closed.

{% endraw %}
```
{: .line-numbers}

