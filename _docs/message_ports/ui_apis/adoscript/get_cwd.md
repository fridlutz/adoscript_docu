---
layout: commandcall
category: CommandCall
title: "GET_CWD"
tags: 1.3 1.5
---

GET_CWD returns the current working directory as an absolute path

# Syntax:  

```adoscript
{% raw %}
CC " AdoScript" GET_CWD .

# --> RESULT cwd:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  



# Returns:  

|`cwd`|strValue, the absolute path to the current working directory|

# Remarks:



# See Also:  

[SET_CWD](set_cwd.html "SET_CWD")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" GET_CWD
CC "AdoScript" INFOBOX ("The current working directory is: " + cwd)

{% endraw %}
```
{: .line-numbers}
displays the current working directory it in an infobox  
