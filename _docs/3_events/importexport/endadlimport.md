---
layout: event
category: Event
title: "EndADLImport"
tags: 1.3 1.5
---

This event is triggered after the ADL import has finished.  

# Parameters:  

|`successful`|intValue, 1 if the import succeeded and 0 if not|

Exit value:



# Remarks:  



# See Also:  

[StartADLImport](startadlimport.html "StartADLImport")  


Example:  

```adoscript
{% raw %}
	ON_EVENT "EndADLImport" {
	
	SET int_Success: (successful) 
	
	IF (int_Success = 1) {
	CC "AdoSript" INFOBOX "You have imported the ADL successfully"
		}
	ELSEIF (int_Success = 0) {
	CC "AdoSript" INFOBOX "Try again!"
		}
	
	}
{% endraw %}
```
{: .line-numbers}

