---
layout: commandcall
category: CommandCall
title: "SET_EXPR_UPDATE"
tags: 1.3 1.5
---

The command SET_EXPR_UPDATE allows you to change the behaviour of the expression manager in ADOxx. The expression manager is responsible for calculating the results of EXPRESSION attributes.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_EXPR_UPDATE synchronous:( 0 | 1 ) asynchronous:( 0 | 1 ) count:intValue interval:intValue 

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`synchronous`|intValue,  0 | 1|
|`asynchronous`|intValue,  0 | 1|
|`count`|intValue,|
|`interval`|intValue,|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Single or multiple arguments can be used to change the behaviour of expression updates in ADOxx. When an argument is not passed, its behaviour will not change. E.g. when you don't pass the argument synchronous, synchronous expression updates will remain turned on if they have been turned opn before or off if they have been turned off before.

By passing the argument synchronous, you can turn synchronous updates of expression attributes off (by passing the value 0) and again on (by passing the value 1). After starting ADOxx, synchronous updates are turned on.

By passing the argument asynchronous, you can turn asynchronous updates of expressions off (by passing the value 0) and again on (by passing the value 1). After starting ADOxx, asynchronous updates are turned on.

With the arguments count and interval, you can specify how much idle time is used to asynchronously update expressions in ADOxx. Setting them only takes effect when asynchronous updates are turned on. The argument count specifies how many expression attributes are updated in one interval. With the argument interval you can specify the time intervals (measured in ms) in which expressions are updated. The real time can be longer depending on the computational load placed on the computer by user input and other processes. The iterval must be set to a positive number greater than or equal to 20. Default values are 5 expressions every 20 ms.

When your application library uses very complex expressions, you can use this command to increase performance by changing the expression updates. When you specify a value too small for count, ADOxx will take a very long time to update expressions. When you specify a value too big for count, ADOxx will spend lots of time calculating expressions and the user will experience delays when modeling in ADOxx. See Example 2.

# See Also:  

[GET_EXPR_UPDATE](get_expr_update.html "GET_EXPR_UPDATE")  


Example 1:

Change the behaviour of the expression manager after ADOxx has started  
```adoscript
{% raw %}

ON_EVENT "AppInitialized"
{
  CC "Core" SET_EXPR_UPDATE synchronous:0 count:1 interval:100
}

{% endraw %}
```
{: .line-numbers}
The command is executed ADOxx has been initialized. No expression attributes will be updated synchronously. Asynchronous updating of expressions is restricted to 1 expression every 100ms.

Example 2:

Bad arguments  
```adoscript
{% raw %}

CC "Core" SET_EXPR_UPDATE count:1000 interval:10000

CC "Core" SET_EXPR_UPDATE count:1 interval:20

{% endraw %}
```
{: .line-numbers}

Approximately every 10 seconds, ADOxx will calculate 10.000 expressions. In models with lots of expressions, this configuration will lead to bad performance because every 10 seconds, ADOxx will freeze and refuse user input because it is recalculating 10.000 expressions.

Every 20ms, ADOxx will re-calculate 1 expression. In models woth lots of expressions, it will take very long to recalculate all stale expressions. In fact ADOxx will hardly ever be able to recalculate all expressions in the model as all expressions are marked stale after modeling operations.  
