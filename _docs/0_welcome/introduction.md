---
layout: generic
category: Support
tags: 1.3 1.5
---

# What is AdoScript  


AdoScript is the scripting language of ADOxx. It is based on LEO, is build procedural, and allows extension possibilities with low programming effort.  
Through AdoScript the user has access to a rich number of ADOxx functionalities.  

# Usage of AdoScript  
AdoScript can  be executed on different ways, so it can be used where it is needed.  

As menu entry:  

For manual execution  (e.g. transformation procedures, evaluation scenarios)  

In events:  

If specific actions are executed, an AdoScript can be automatically called.  
(e.g. a special dialogue replaces the standard dialogue window)  

In the Notebook via Programmcall:  

Similar as for menu entries, but triggered from within the Notebook.  

Automatically over Command Prompt:  

Trigger during startup of ADOxx and handover of AdoScript through the command prompt.  

From AdoScript-Shell:  

As a debugging and development facilities to test code snipplets.  

# Integration of AdoScript  
AdoScript builds on the so-called "Message Port-Concept". That means messages are sent  
to specific ports and return result messages for further usage and application


![](/images/AS_Overview.png)

# Programmable through scripting APIs  
Method-specific development of functionalities is possible through scripting techniques.  
Function calls/APIs of the platform (realized in C++) are possible through scripting language  
AdoScript. AdoScript "Messageports"/APIs are categorized according to components


|Component APIs|UI APIs|Manipulation APIs|Application APIs|  
|:--------|:-------:|--------:|--------:|  
|Messageport Acquisition|Messageport AdoScript|Messageport Core|Messageport Drawing  
|Messageport Modeling|Messageport CoreUI|Messageport DB|Messageport Application  
|Messageport Analysis|Messageport Explorer|Messageport UsrMgt  
|Messageport Simulation||||  
|Messageport Evaluation||||  
|Messageport ImportExport||||  
|Messageport Documentation||||  
|Messageport AQL||||


# Useful Tips  

- **Every Command Call stores the result in global variables:**  

Right after the CC store the required global variables in local variable to avoid overwriting them  
during the next CC  

- **Tracking  the global variables with "debug":**  

Use the keyword debug during CC to track the status of variables:  "CC "xxx" debug" COMMAND  

- **Variables are allocated with values, distinguish if you manipulate the variable v1, or the value of the variable (v1):**  

Use VAL and STR to convert strings to integer and vice versa.  

Use tokcnt to count tokens in a result list.  

Use () to get the value of a variable.  

Use CM to convert into centimeters.


# Improvements  

Please provide your feedback and improvement suggestions for the AdoScript documentation via email to faq@adoxx.org.  




