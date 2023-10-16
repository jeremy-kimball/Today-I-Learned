*Dependency Inversion Principle* (DIP) is the final principle of SOLID, which are the essential building blocks of object-oriented programming and design. The Dependency Inversion Principle promotes the decoupling of high-level modules from low-level modules by introducing abstractions.

## DIP Benefits
* Decoupling - Adherance to DIP promotes modularity making the code easier to maintain and extend.
* Testability - Decoupled code can be tested independently. 
* Reusability - Without reliance on other code modules can be reused easier.

## Example
These classes do not follow the “Dependency Inversion Principle” as the higher-level class EmployeeDetails is directly dependent upon the lower-level SalaryCalculator class.
```
// Not following the Dependency Inversion Principle
public class SalaryCalculator
{
    public float CalculateSalary(int hoursWorked, float hourlyRate) => hoursWorked * hourlyRate;
}
public class EmployeeDetails
{
    public int HoursWorked { get; set; }
    public int HourlyRate { get; set; }
    public float GetSalary()
    {
        var salaryCalculator = new SalaryCalculator();
        return salaryCalculator.CalculateSalary(HoursWorked, HourlyRate);
    }
}
```
Below, an interface ISalaryCalculator is created, and then we have a class called SalaryCalculatorModified that implements this interface. Finally, in the higher-level class EmployeeDetailsModified, we only depend upon the ISalaryCalculator interface and not the concrete class. Hence, when we create the EmployeeDetailsModified class, we specify the abstraction implementation to use. In addition to this, the details of the CalculateSalary function are hidden from the EmployeeDetailsModified class, and any changes to this function will not affect the interface being used. Hence, we can see that in this new design, the higher-level class does not depend upon the lower-level class but on an abstraction, and the abstraction does not depend upon the details.
```
// Following the Dependency Inversion Principle
public interface ISalaryCalculator
{
    float CalculateSalary(int hoursWorked, float hourlyRate);
}
public class SalaryCalculatorModified : ISalaryCalculator
{
    public float CalculateSalary(int hoursWorked, float hourlyRate) => hoursWorked * hourlyRate;
}
public class EmployeeDetailsModified
{
    private readonly ISalaryCalculator _salaryCalculator;

    public int HoursWorked { get; set; }
    public int HourlyRate { get; set; }
    public EmployeeDetailsModified(ISalaryCalculator salaryCalculator)
    {
        _salaryCalculator = salaryCalculator;
    }
    public float GetSalary()
    {
        return _salaryCalculator.CalculateSalary(HoursWorked, HourlyRate);
    }
}
```

## Things to Note
### How does Dependency Inversion Principle differ from Dependency Injection?
The Dependency Inversion Principle focuses on making high-level and low-level modules depend on abstractions, while Dependency Injection is a technique for providing these abstractions to the modules at runtime.
### Why are interfaces important in implementing the Dependency Inversion Principle?
Interfaces act as abstractions that both high-level and low-level modules depend on, allowing for easy decoupling and flexibility. They play a crucial role in implementing the Dependency Inversion Principle in C# and other object-oriented programming languages.
### What are the High-Level and Low-Level Modules
* The high-level modules describe those operations in our application that have more abstract nature and contain more complex logic. These modules orchestrate low-level modules in our application.
* The low-level modules contain more specific individual components focusing on details and smaller parts of the application. These modules are used inside the high-level modules in our app.


















---
Sources \
[Bytehide](https://www.bytehide.com/blog/dependency-inversion-principle-in-csharp-solid-principles) \
[c-sharpcorner](https://www.c-sharpcorner.com/article/solid-principles-in-c-sharp-dependency-inversion-principle/) \
[Code-maze](https://code-maze.com/dependency-inversion-principle/) 
