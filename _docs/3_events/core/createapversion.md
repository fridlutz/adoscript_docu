---
layout: event
category: Event
title: "CreateAPVersion"
tags: 1.3 1.5
---

This event is triggered after an AttrProf version was created.  

# Parameters:  

|`apthreadid`|intValue, contains the ID of the AttrProf thread to which the version was attached.|
|`apversionstr`|intValue, contains the version string of the newly created AttrProf version|
|`apversionid`|intValue, contains the ID of the created AttrProf version.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "CreateAPVersion" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

