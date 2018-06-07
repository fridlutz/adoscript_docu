---
layout: commandcall
category: CommandCall
title: "CC"
tags: 1.3 1.5
---

Is used for executing an ADOxx command call.

# Syntax:  

```adoscript
{% raw %}
CC strValue [ var:varName ] [ debug ] [ raw ] <command>
{% endraw %}
```
{: .line-numbers}
# Parameters:  

|`<main_parameter>`|strValue, the name of the message port|
|`debug`|modifier, if specified in a CC command, the RESULT string is shown in an info box. This may be helpfull for bug searching. If the variable ccdebug is set to "always", the info box is shown always, even if debug is not specified. If the variable ccdebug is set to "never", the info box is never shown. If ccdebug is undefined or has any other value but "always" or "never" (e.g. ""), the info box is shown exactly if debug is specified. If the variable ccdebugfile is set, the debug information is written into a file instead of being shown in an info box. The value of ccdebugfile must be a filename (writing to that file) or an empty string (showing info boxes).|
|`raw`|modifier, if specified, CC sends the message without previously evaluating expressions and substituting them by their current result value. This is needed when a message shall be sent which is containing AdoScript code.|
|`var`|modifier, if a variable is specified with var, CC does not copy each result value into a separate runtime variable. Instead just one object value is created for the specified variable which contains all result values with the result parameter names as properties.|
|`<command>`|is a command call as described in this documentation|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:

If the answer of a message is, for example,   RESULT ecode:0 val:"Madrid"   , CC with var:result creates an object variable **result** with properties result.ecode = 0 and result.val = "Madrid". The benefit of this "modern" way to use CC is that the current runtime variable set is not polluted with several result variables. Instead always exactly one local variable is set. This programming style is much clearer for readers of the source code and it is also less error-prone. If a command call is being extended for a newer ADOxx version, there may be introduced some additional return parameters. Such new parameters can make a script incompatible when new return parametes are already used as runtime variables in an older script.

The LEO element (&lt;command&gt;) after the CC element is called message element and does not really belong to the AdoScript syntax, i.e. it would cause a syntax error without the leading CC element . The benefit of the CC form above is that the string does not have to be masked. If there are more parameters, maybe some of them as expressions, it is easier to write the "natural" LEO element than to construct a string which will be a LEO element. Expressions in the message element are evaluated before the message is sent. An example for that is given below.

# See Also:  

[SEND](send.html "SEND")  


Example 1:

```adoscript
{% raw %}

CC "Core" GET_ATTR_VAL objid:(objid) attrid:(attrid)
IF (ecode > 0) ...

{% endraw %}
```
{: .line-numbers}

Example 2:

Classic way to use CC "Core" GET_ATTR_VAL  
```adoscript
{% raw %}

CC "Core" GET_ATTR_VAL objid:(objid) attrid:(attrid)
IF (ecode = 0) {
    CC "AdoScript" INFOBOX ("Value: " + val)
} ELSE {
    CC "AdoScript" ERRORBOX ("Error: " + errtext)
}

{% endraw %}
```
{: .line-numbers}

Modern form  
```adoscript
{% raw %}

CC "Core" var:result GET_ATTR_VAL objid:(objid) attrid:(attrid)
IF (result.ecode = 0) {
    CC "AdoScript" INFOBOX ("Value: " + result.val)
} ELSE {
    CC "AdoScript" ERRORBOX ("Error: " + result.errtext)
}

{% endraw %}
```
{: .line-numbers}

Example 3:

Debugging  
```adoscript
{% raw %}

CC "Core" debug GET_ATTR_VAL objid:(objid) attrid:(attrid)
SET ccdebugfile:"d:\\ccdebug.log"
CC "AdoScript" debug FILE_COPY from:"ei1.txt" to:"ei2.txt"
SET ccdebugfile:""

{% endraw %}
```
{: .line-numbers}

