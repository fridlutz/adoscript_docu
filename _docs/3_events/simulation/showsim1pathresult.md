---
layout: event
category: Event
title: "ShowSim1PathResult"
tags: 1.3 1.5
---

This event is triggered when the button "Path results" has been hit in the path analysis result window.  

# Parameters:  

|`simpath`|strValue, holds the IDs of all objects and connectors (alternately) in the current path. IDs from one model are always kept together. The string starts with the IDs from the main process. (Example: &lt;IDs from main process&gt; &lt;IDs from subprocess 1&gt; &lt;IDs from subprocess 2&gt; ...). Before each subprocess ID the call path is given (Example: &lt;Main model ID&gt; &lt;ID of submodel A (first layer)&gt; &lt;ID of submodel B (second layer)&gt; &lt;ID of first object in submodel B&gt; ...).|
|`pathprob`|realValue, probability of the current path.|
|`pathcycletime`|realValue, cycle time of the current path in seconds|
|`simruns`|intValue, number of simulation runs.|

Exit values:

|`0`|()default) the standard simulation result window will be displayed (and the path will be marked in the model window)|
|`1`|the standard behaviour will not be executed.|

# Remarks:  

The standard form     **EXIT** intValue   should be used for returning a result.  

# See Also:  

[EXIT](exit.html "EXIT")  


Example :

```adoscript
{% raw %}

ON_EVENT "ShowSim1PathResult"
  {
    # Initialization (just in case...):
    IF (type (specialsimres) = "undefined")
    {
      SETG specialsimres:0
    }

    # Here starts the important stuff.
    IF (specialsimres = 1)
    {
      # The simulation was started from the AdoScript "My special path analysis", so lets display the results
      # in our "special" own format. The code for this is read from the external file "showresults.asc" (see
      # below).
      # Important note: The AdoScript from the file has to be executed with scope:same because otherwise
      # the automatically set variables of this event which contain the result information would not
      # be accessible:
      CC "AdoScript" FREAD file:("showresults.asc")
      EXECUTE (text) scope:same

      # Skip the standard result displaying behaviour because we have already displayed the
      # result in our own format...:
      SET return:(1)
    }
    ELSE
    {
      # The simulation was started via the normal menu entry.
      # So let's use the standard result displaying behaviour:
      SET return:(0)
    }
  }

{% endraw %}
```
{: .line-numbers}

