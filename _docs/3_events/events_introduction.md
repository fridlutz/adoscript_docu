---
layout: generic
category: Support
tags: 1.3 1.5
---

Event Handlers are AdoScripts which are executed when certain events occur (e.g. loading a model,  
create an instance, edit an attribute value,...) depending on the event, a certain set of parameters/variables  
are predefined to be used during the implementation of the actual handler. The implemantation is done in the  
Library Attribute "Add Ons" of the dynamic sublibrary and are build as follows

```adoscript
{% raw %}

	ON_EVENT "AppInitialized" { 

	#do smthg.

	}
{% endraw %}
```
{: .line-numbers}

In ADOxx event handlers are used to:

-Listen to events that result from the interaction with of the modelling toolkit

-Handle/Trigger operations based on the events  

The possible events are categorised after their place of activity:

-Application  

-Core  

-Drawing  

-ImportExport  

-Modeling  

-Simulation  

