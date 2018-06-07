---
layout: commandcall
category: CommandCall
title: "SEND"
tags: 1.3 1.5
---

Is used for sending an ADOxx command call to an ADOxx message port.

# Syntax:  

```adoscript
{% raw %}
SEND strValue to:msgPortName [ answer:varName ] .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, contains the command to be sent to the message port|
|`to`|strValue, the name of the message port|
|`answer`|varName, a variable where the result of the command is stored|

# Returns:  

none

# Remarks:

MessagePorts are internal instances in ADOxx which are part of a component and receive strings (messages) which contain component-specific commands. Actually a message is a LEO text.

When a message is received the MessagePort decodes it and executes the desired command. Some MessagePort commands return a value which can be assigned to a run-time variable using answer in the SEND command. Mostly the return value is also a LEO text, which makes it possible that structured values are returned.

The MessagePort (specified with **to** in the SEND command) can be one of the following:  
"AdoScript" - some usefull general Dialogs;  
"Core" - interface to the core  
"CoreUI" - interface to core ui modules (e.g. model select box)  
"Application" - interface to the application and its main window  
"Acquisition" - interface to the acquisition component  
"Modeling" - interface to the modeling component  
"Analysis" - interface to the analysis component  
"Simulation" - interface to the simulation component  
"Evaluation" - interface to the evaluation component  
"ImportExport" - interface to the import/export component  
"Documentation" - interface to the docu component  
"AQL" - interface to the AQL engine  
"UserMgt" - interface to the user management component  
"Drawing" - interface to the drawing component  
"DB" - interface to the database component  
"Explorer" - interface to the ADOxx Explorer

# See Also:  

[CC](cc.html "CC")  


Example 1:

```adoscript
{% raw %}

SEND ("GET_ATTR_VAL objid:" + STR objid + " attrid:" + STR attrid) to:"Core" answer:text
LEO parse:(text) get-int-value:ecode:"ecode" get-str-value:val:"val"
IF (ecode > 0) ...

{% endraw %}
```
{: .line-numbers}

