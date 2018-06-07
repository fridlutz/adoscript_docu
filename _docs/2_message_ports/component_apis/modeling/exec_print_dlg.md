---
layout: commandcall
category: CommandCall
title: "EXEC_PRINT_DLG"
tags: 1.3 1.5
---

EXEC_PRINT_DLG shows a modal dialog for printing a model.  
This command returns ecode 0 if it was executed successfully and ecode 1 if there was an error.  
The ecode does not say anything about whether the user executed or canceled the print dialogue.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" EXEC_PRINT_DLG [ modelid:id ] 
							 [ printer:strValue ] 
							 [ layout:strValue ]
							 [ Scaling ] 
							 [ orientation:Orientation ] 
							 [ auto-execute ] .


Scaling :	factor:intValue |
fitonepage |
pages-height:intValue |
pages-width:intValue .


Orientation :	"automatically" | "portrait" | "landscape" .


-->RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, modelid ID of the model that shall be printed.|
|`printer`|strValue, the name of the selected printer (with path).|
|`layout`|strValue, name of the selected page layout.|
|`factor`|intValue, a certain scaling factor as percent value.|
|`fitonepage`|modifier, the scaling factor is computed by the "fit one page" method.|
|`pages-height`|intValue, the scaling factor is computed by the "fit height of &lt;n&gt; pages" method.|
|`pages-width`|intValue, the scaling factor is computed by the "fit width of &lt;n&gt; pages" method.|
|`orientation`|Orientation, the paper orientation.|
|`auto-execute`|modifier, model is printed directly with the given parameters (without executing the dialog at all).|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

If no model ID is specified, the model of the active model window is taken. Specifying an ID after the keyword (without "modelid:") has the same meaning, but is deprecated.  

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" EXEC_PRINT_DLG

{% endraw %}
```
{: .line-numbers}


