---
title: "C# Interview #1: Exception handling"
tags:
---

<!-- more -->
### Overview

Attending the job interviews is a great inspiration for blog post ideas. I've noticed this reoccurring theme - handling exceptions. That's why I thought it'd be nice to make it easily "googleable" - we're going to take a look on how to handle exceptions in C# and how to apply it in real life scenario of a web application.
<!-- excerpt -->

### A bit of theory

There are a few basic things you need to know about exceptions. Why do we even bother? Well, there are scenarios that even most sophisticated piece of software can't handle. For example - what do you think happens when you attempt to divide by zero an int or a Decimal value? The environment will _throw_ an exception DivideByZeroException(more about this you can read more about it [here](https://docs.microsoft.com/en-us/dotnet/api/system.dividebyzeroexception?view=netframework-4.8)). Pretty straight forward - the title tells you what's the problem, the debugging tools can be configured to stop the execution on the exception occurrence, which helps the developer identify the placement and cause of the exception. 

As a developer, you can define custom scenarios that should stop a regular execution of your code. By throwing an exception you ensure that the code doesn't run under unwanted circumstances. The C# language provides the `throw` keyword, which needs to be followed by a object of a class deriving from `System.Exception`. You can use the class's constructor to  

Alright, but how do we deal 

### Exception cascade
Let's take a look at the simple code below

{% codeblock Exception example no. 1 lang:CSharp %}
var numbers = new string[] { "1", "2", "3.05", "Four", "5", "Giraffe"};

try
{
    foreach (var number in numbers)
    {
        var parsedNumber = int.Parse(number);
        Console.WriteLine($"Number {parsedNumber} was successfully parsed");
    }
}
catch
{
    Console.WriteLine("An exception was thrown");
}
{% endcodeblock %}

