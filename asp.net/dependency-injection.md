## Dependency Injection in an [ASP.NET](https://github.com/dotnet/aspnetcore) Core App [^1][^2][^3][^5]

Dependency Injection is a software design pattern intended to achieve Inversion of Control (IoC). Dependency can cause issues like difficulty refactoring and trouble testing. Instead of an object creating objects it needs manually inside its class, the dependency object is created outside and passed in. This leads to a separation of concerns as the dependent class doesn’t need to concern itself with how a dependency is created, just how it uses it.

# Advantages
* Cleaner Code
  * Dependency injection helps with this by decoupling the dependent from the dependency. Being able to follow a pattern of dependent to dependency through injections provides an easy way to follow exactly the classes function.
* Testing
  * Dependencies are hard to mock for unit testing. By Injecting interfaces of dependencies you can provide a “test double” for an injected interface.
* Maintainability
  * The example given in MethodPoet[^4] helps to highlight this point better than I think I am able to in my own words.
    > “You have a website application that uses MySQL as a database. Then someone makes a decision that the website should use the MS SQL database instead. If your database layer is isolated behind an interface, then no problem. You just create a new implementation of the database layer and you are done. However, if your SQL code is everywhere throughout the app, you will have difficulty explaining why you need so much time to change one database for another.”
# Disadvantages
* Complexity
  * The added number of classes due separation of responsibilities can sometimes be a hindrance instead of a benefit. Especially in very small projects.
* Performance
  * Although from my research[^6] it seems to be of minor concern, there is a small decrease in performance.
* Dependency on a framework
  *  Although it doesn’t seem to be the case as much for C# as a dependency injection framework is part of the .NET, dependency on a framework like [spring](https://github.com/spring-projects/spring-framework) for example introduces potential issues like incompatibility with versions or having to dive through large documentation of the framework to track down issues.
 
# Example
In our controller classes we are injecting the interface `ILogger<HomeController>` in the constructor for the controller. <br><br>
![image](https://github.com/jeremy-kimball/Today-I-Learned/assets/130601077/14879a26-70d5-499c-b98e-659cc939fb79)
<br><br>
`ILogger` allows for logging and customizing the error messages you store, making it much easier to identify bugs in your application. This is framework that is included in C# .Net, however you may want to use different logging frameworks to better suit your purposes and with dependency injection you are able to do so easily by implementing the appropriate interfaces and injecting them with constructor injection in your controller.

[^1]: https://www.dotnettricks.com/learn/dependencyinjection/implementation-of-dependency-injection-pattern-in-csharp
[^2]: https://en.wikipedia.org/wiki/Dependency_injection
[^3]: https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection
[^4]: https://methodpoet.com/dependency-injection-benefits/#5_benefits_of_using_dependency_injection_in_your_C_code
[^5]: https://www.claudiobernasconi.ch/2019/01/24/the-ultimate-list-of-net-dependency-injection-frameworks/
[^6]: https://medium.com/@szntb/the-dark-side-of-dependency-injection-5c673f3ed751
