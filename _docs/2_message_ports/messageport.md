---
layout: generic
category: Support
tags: 1.3 1.5
---

# MessagePorts  
MessagePorts are internal instances in ADOxx. These instances are parts of any component and receive strings  
containing component-specific commands. Actually a message is a LEO text.  
When a message is received, the MessagePort decodes it and executes the desired command.  
Some commands return a value. Mostly the return value is also a LEO text, which makes it  
possible that structured values are returned.  
Sending messages can be achieved in AdoScript using SEND or CC. CC is generally preferred.  
One advantage of this command is the handling of a returned LEO text, i.e. assigning encoded values  
to runtime variables, which is done by CC completely.

# Structure

The constructs needed to call a command are

CC + "Messageport":

Every call has to start with the CC  -"Call Command" and the respective Messageport.

API Command:  
the command is specified in CAPITAL letters. In case the command should be run in debug mode,  
add "debug" between the Messageport and the command. This results in a pre-execution of the command including  
the possibility to view input and result values before actual execution.

Input Values:

if needed according to API signature

Result Value:

as produced by the command

![](/images/AdoScriptCommand.png)

# AdoScript Basics

_Variable_declaration_:  

```adoscript
{% raw %}
		SET, LEO
{% endraw %}
```
{: .line-numbers}

Control structures:  

```adoscript
{% raw %}
		IF/ELSIF/ELSE, WHILE, FOR, BREAK, EXIT, PROCEDURE, FUNCTION
{% endraw %}
```
{: .line-numbers}

External programs/File callings(AdoScript, EXE, DLL):  

```adoscript
{% raw %}
		EXECUTE, SYSTEM, START, CALL
{% endraw %}
```
{: .line-numbers}

Sending of messages to ADOxx Component (Messageports):  

```adoscript
{% raw %}
		CC, SEND
{% endraw %}
```
{: .line-numbers}

LEO Expressions:  

Usage of expressions for call parameters.

# AdoScript Operators

Logical:  

```adoscript
{% raw %}
		AND, OR, NOT
{% endraw %}
```
{: .line-numbers}

Comparison:  

```adoscript
{% raw %}
		< , > , <= , >= , = , <> , !=
{% endraw %}
```
{: .line-numbers}

Arithmetical:  

```adoscript
{% raw %}
		+ , - , ** , / , - (unary)
{% endraw %}
```
{: .line-numbers}

Strings:  

```adoscript
{% raw %}
		s + t , n ** s , s / t , s SUB i , LEN s
{% endraw %}
```
{: .line-numbers}

Conversions:  

```adoscript
{% raw %}
		STR value , VAL string
{% endraw %}
```
{: .line-numbers}

# AdoScript Functions

Arithmetical:  

```adoscript
{% raw %}
		abs(x), max(x, y), min(x, y), pow(x, y), sqrt(x), exp(x), log(x), log10(x)
{% endraw %}
```
{: .line-numbers}

Strings:  

```adoscript
{% raw %}
		search(source,pattern,start)
		
		bsearch(source,pattern,start)
		
		copy(source,from,count)
		
		replall(source,pattern,new)
		
		lower(source)
		
		upper(source)
{% endraw %}
```
{: .line-numbers}

Lists:  

```adoscript
{% raw %}
		token(source,index[,separator])
		
		tokcnt(source[,separator])
		
		tokcat(source1,source2[,separator])
		
		tokdiff(source1,source2[,separator])
		
		tokisect(source1,source2[,separator])
		
		tokunion(source1,source2[,separator])
{% endraw %}
```
{: .line-numbers}

# AdoScript: Procedure Concept  

| ProcedureDefinition | PROCEDURE [global] ProcedureName[MainParameter]{FormalProcParameter}{StatementSequence}  
| MainParameter | TypeName: paramName  
| FormalProcParameter | paramName:TypeNameOrReference  
| TypeNameOrReference | TypeName | reference  
| TypeName | string | integer | real | measure | time |array | expression | undefined  
| ProcedureName | keyword  
| ProcedureCall | anyLeoElement  

Example:  

```adoscript
{% raw %}
			PROCEDURE MYPROC integer: n val: string result: reference
			{
			SET result: (val + STR n)
			} 
{% endraw %}
```
{: .line-numbers}


# AdoScript: Functions concept

| FunctionDefinition : | FUNCTION functionName[:global] { FormalFuncParameter } return:expression  
| FormalFuncParameter :| paramName:TypeName  
| TypeName :| string | integer | real | measure | time | expression | undefined  

Example:  

```adoscript
{% raw %}
			FUNCTION fak n: integer
			return: (cond (n <= 1, 1, n ** fak (n -1)))
			SET m: (fak (10)) 
{% endraw %}
```
{: .line-numbers}

# Expressions in AdoScript

Expressions can be used direct as arguments in calls.

Use closures () in order to delineate arguments of an expression.

Examples :  
```adoscript
{% raw %}
		
		SET n:(copy (vn, 0, 1) + ". " + nn)
 
		IF ( cond( type( n ) = "integer", n = 1, 0 ) )
		{
		...
		}
		
		EXECUTE ("SET n:(" + n + ")")
{% endraw %}
```
{: .line-numbers}

# AdoScript Programming Guidelines

If your are programming AdoScript, please consider following rules:

-Files which contain AdoScript should be named file.asc.  

-The returning result of a message port command should be copied and commented on the line below the command

```adoscript
{% raw %}
		GET_CLASS_NAME classid: intValue
			# --> RESULT ecode:intValue classname:strValue isrel:intValue 
{% endraw %}
```
{: .line-numbers}

-Indent a block with two spaces.  

-Don‘t use the tabulator to indent blocks.  

-Decompose the complexity of the programm by using procedures and functions.  
