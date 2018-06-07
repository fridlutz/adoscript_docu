---
layout: commandcall
category: CommandCall
title: "EXEC_MENUENTRY"
tags: 1.3 1.5
---

EXEC_MENUENTRY starts the documentation export for the menu entry specified as main parameter

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" EXEC_MENUENTRY strExpr [ no-interref-warnings ]

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main-parameter>`|strExpr, holds the name of the menu entry that should be called.|
|`no-interref-warnings`|modifier, suppresses error messages caused by dangling interrefs.|
# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Calling EXEC_MENUENTRY has the same effect as clicking on the menuentry in the documentation menu.

In ADOxx, interref attributes may point to models that are no longer existing. When exporting with the option "with referenced models", ADOxx displays the error message [asgmlexp-08] whenever such an interref is encountered. By specifying no-interref-warnings, such error messages will not be displayed.

# See Also:  



Example 1:

Starts the menu entry "HTML-Generation...". If the user clicks "Cancel" in the export dialog or the documentation generation fails, an INFOBOX is displayed.

```adoscript
{% raw %}

CC "Documentation" EXEC_MENUENTRY "HTML-Generierung..."
IF (ecode = 0)
{
   CC "AdoScript" INFOBOX "Documentation-generation was aborted!"
}

{% endraw %}
```
{: .line-numbers}

