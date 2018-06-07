---
layout: commandcall
category: CommandCall
title: "EXECUTE"
tags: 1.3 1.5
---

EXECUTE executes dynamicly a new script which can be read from a file or composed by an expression.

# Syntax:  

```adoscript
{% raw %}
EXECUTE Source 	[ scope: separate | same | child | default ] 
				[ result:varName ]

Source :	file:strValue | strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, an AdoScript to be executed. Can be replaced by the parameter file.|
|`file`|strValue, the path and filename of a file containing an AdoScript.|
scope - is a keyword defining the scope for the AdoScript to be executed; scope:separate - lets the execution be performed in a new scope which does not have access to any other scope but global variables; scope:child - the scope of the subprogram is a child of the current scope; scope:same - lets the execution be performed in the scope of the EXECUTE call; scope:default - if scope has the value "child" or "same" this means the same as scope:child or scope:same, otherwise the scope:separate behaviour is applied; if none specified, scope:default is applied.
|`result`|varName, is assigned the exit value of the executed script.|
# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:

The exit value is the value after the EXIT keyword with which the executed script has been exited. If the script has terminated without EXIT, the exit value is 0.



# See Also:  

[EXIT](exit.html "EXIT")  


Example 1:

Executing a script which comes from a file  
```adoscript
{% raw %}

EXECUTE file:"d:\\test.asc"

{% endraw %}
```
{: .line-numbers}

Example 2:

Simple AdoScript shell  
```adoscript
{% raw %}

CC "AdoScript" EDITBOX title:"AdoScript"
IF (endbutton = "cancel") {
  EXIT
}
EXECUTE (text)

{% endraw %}
```
{: .line-numbers}
lets the user enter any text which is interpreted as a new script and executed.

