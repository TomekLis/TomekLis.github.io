---
title: "C# Interview #1: Exceptions"
thumbnailImage: https://helpx.adobe.com/content/dam/help/en/stock/how-to/visual-reverse-image-search/jcr_content/main-pars/image/visual-reverse-image-search-v2_intro.jpg
thumbnailImagePosition: bottom
# coverImage: 2019-09-19 20_02_04-hexo.png
# auto_thumbnail_image: true
tags:
---

### Overview

Job interviews is are great inspiration for blog post ideas. I've noticed this reoccurring theme - handling exceptions. That's why I thought it'd be nice to make it easily "googleable" - we're going to take a look on how to handle exceptions in C# and how to apply it in real life scenario of a web application.
<!-- more -->

### Throwing exceptions

There are a few basic things you need to know about exceptions. Why do we even bother? Well, there are scenarios that even most sophisticated piece of software can't handle. For example - what do you think happens when you attempt to divide by zero? The environment will _throw_ an exception DivideByZeroException(more about this you can read more about it [here](https://docs.microsoft.com/en-us/dotnet/api/system.dividebyzeroexception?view=netframework-4.8)). Pretty straight forward - the title tells you what's the problem, the debugging tools can be configured to stop the execution on the exception occurrence, which helps to identify the placement and cause of the problem. 

You can define custom scenarios that should stop a regular execution of your code. By throwing an exception you ensure that the code doesn't run under unwanted circumstances. The C# language provides the `throw` keyword, which needs to be followed by a object of a class deriving from `System.Exception`. You can use the class's constructor to provide some useful message explaining the cause of the exception. See the example below.
{% codeblock lang:CSharp %}
var colors = new string[] { "blue", "yellow", "green" }; 

if (!colors.Contains("grey"))
{
    throw new Exception("The colors array is missing grey");
}
{% endcodeblock %}
Let's see how the Visual Studio debugger behaves when running into this code.
{% image "2019-09-19 20_02_04-hexo.png" %}
As mentioned before - the 

### Handling expiations
Alright, but have to deal with the exceptions somehow. That's where the `try`, `catch` and `finally` keywords come in handy. We use the `try` keyword to cover the code where we expect the exceptions to occur.  

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

