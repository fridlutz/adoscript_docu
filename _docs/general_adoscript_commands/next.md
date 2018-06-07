---
layout: commandcall
category: CommandCall
title: "NEXT"
tags: 1.3 1.5
---

With NEXT the next loop for the enclosing WHILE or FOR statement is executed.

# Syntax:  

```adoscript
{% raw %}
NEXT
{% endraw %}
```
{: .line-numbers}

# Parameters:  



# Returns:  



# Remarks:



# See Also:  

[FOR-string token form](for-string_token_form.html "FOR-string token form")  
[FOR-numerical form](for-numerical_form.html "FOR-numerical form")  
[WHILE](while.html "WHILE")  
[BREAK](break.html "BREAK")  


Example 1:

```adoscript
{% raw %}

SET i:0
WHILE (i < 5)
{
   SET i:(i+1)
   IF (i = 2)
   {
      NEXT
   }
   CC "AdoScript" INFOBOX ("Test: " + STR i)
}

FOR i from:1 to:5
{
   CC "AdoScript" INFOBOX ("Test: " + STR i)
   NEXT
   CC "AdoScript" INFOBOX ("Error, is never reached: " + STR i)
}

FOR i from:1 to:2
{
   FOR t in:"a b"
   {
      IF (i > 1 AND t = "a")
      {
         NEXT
      }
      CC "AdoScript" INFOBOX ("Test: " + STR i + " " + t)
   }
}

{% endraw %}
```
{: .line-numbers}

