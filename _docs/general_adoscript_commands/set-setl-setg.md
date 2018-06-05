---
layout: commandcall
category: CommandCall
title: "SET / SETL / SETG"
tags: 1.3 1.5
---

SET assigns values to new or existing AdoScript runtime variables. A variable's lifetime usually is the execution of the current AdoScript or procedure.

Using SETG lets the variable exist for the whole ADOxx session, so it can be reused in successing executions of the same or other AdoScripts.

If a variable exists in the current scope, SET overwrites its value. If a variable should generally be local, also if a same-name variable already exists in a higher scope, SETL has to be used.

# Syntax:  

```adoscript
{% raw %}
SET { VarAssignment }

SETL { VarAssignment }

SETG { VarAssignment }

VarAssignment :	LValue : anyExpr .

LValue :	varName | ArrayLValue .

ArrayLValue :	varName [ CommaExpr ] .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

It is recommended to initialize all variables with SETL unless there is a reason not to do so. Otherwise there might be the risk of changing a variable which you did not think of. If a variable v is used by a procedure P, and P calls another procedure Q, then Q can change v. So, only if SETL is used for initializing v in Q, you can be sure that such a case will not happen.

SET allows also to change elements of an existing array. [...]

# See Also:  



Example 1:

```adoscript
{% raw %}

# Declares the global variable 'a' and inits it with '0'
SETG a:0

# Prints '0'
CC "AdoScript" INFOBOX (STR a)

SCOPE_TEST

# Prints '1'
CC "AdoScript" INFOBOX (STR a)

EXIT

PROCEDURE SCOPE_TEST {

    # Changes the value of the global variable 'a' to '1'
    SET a:1

    # Prints '1'
    CC "AdoScript" INFOBOX (STR a)

    # Declares the local variable 'a' and inits it with '2'
    SETL a:2

    # Prints '2'
    CC "AdoScript" INFOBOX (STR a)

    # Changes the value of the local variable 'a' to '3'
    SET a:3

    # Prints '3'
    CC "AdoScript" INFOBOX (STR a)
}

{% endraw %}
```
{: .line-numbers}

Example 2:

Counting the number of executions of an AdoScript  
```adoscript
{% raw %}

IF (type (numcalls) = "undefined") {
    SETG numcalls:1
}
ELSE {
    SET numcalls:(numcalls + 1)
}
CC "AdoScript" INFOBOX ("Number of calls: " + STR numcalls)

{% endraw %}
```
{: .line-numbers}

Example 3:

Changing array elements  
```adoscript
{% raw %}

SET a:({"Bonn", "K�ln", "Leverkusen", "Wuppertal"})
SET a[2]:"Siegburg"  # replaces "Leverkusen"
SET b:({{4711, 4712}, {6006, 6007}})
SET b[0, 1]:2011  # replaces 4712
SET b[1]:({7755, 7756})  # replaces {6006, 6007}
SET b[0][1]:2012  # syntax error! [][] just allowed in expressions

{% endraw %}
```
{: .line-numbers}

