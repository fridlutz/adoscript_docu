---
layout: event
category: Event
title: "MOCTimer"
tags: 1.3 1.5
---

This event is triggered periodically each 55ms while the application is in idle state. It makes it possible to call procedures periodically. Another application is delayed execution.  

# Parameters:  

none

Exit value:

none

# Remarks:  



# See Also:  



Example 1:  

Let a class "Clock" have a class attribute "Time" of type STRING. We use the "MOCTimer" event to periodically write the current time into that class attribute  
```adoscript
{% raw %}

ON_EVENT "MOCTimer" {
    CC "Core" GET_CLASS_ID classname:"Clock"
    CC "Core" GET_ATTR_ID classid:(classid) attrname:"Time"
    CC "Application" GET_DATE_TIME time-format:"HH:MM"
    CC "Core" SET_ATTR_VAL objid:(classid) attrid:(attrid) val:(time)
}

{% endraw %}
```
{: .line-numbers}

Now we define a GraphRep which reads the Time class attribute and displays it as a simple analog clock

```adoscript
{% raw %}
GRAPHREP sizing:asymmetrical
SHADOW off
PEN w:0.15cm color:$207060
FILL color:$70c0b0
ELLIPSE x:0cm y:0cm rx:2cm ry:2cm
AVAL set-default:"10:03" time:"Time"
SET zwopi:6.2831853
SET h:(set(v, VAL copy(time, 0, 2)), cond(v >= 12, v - 12, v))
    m:(VAL copy(time, 3, 2))
SET dm:(m / 60) dh:((h ** 60 + m) / 720)
LINE x1:0cm y1:0cm
     x2:(sin(dh ** zwopi) ** 1.4cm) y2:(-cos(dh ** zwopi) ** 1.4cm)
LINE x1:0cm y1:0cm
     x2:(sin(dm ** zwopi) ** 1.8cm) y2:(-cos(dm ** zwopi) ** 1.8cm)
{% endraw %}
```
{: .line-numbers}

All objects of class "Clock" always display the current time now, i.e. a change of the current time (which happens every minute) instantly updates the symbol on the drawing area.

(see: MOCTimer.png)

