# AutoMapper with .NET 7
In this article we try to show what is AutoMapper & How its work with C# .NET 7. 
Using AutoMapper with EntityFramework Core and PostgreSql on Asp.Net Core

# What is AutoMapper

 AutoMapper is a popular object-to-object mapping library in C# for .NET applications. It simplifies the process of mapping properties from one class to another, helping to reduce boilerplate code and streamline development. AutoMapper is commonly used in scenarios where you need to transform objects of one type into objects of another type, which might have similar or different structures.

# Installation

Requires Automapper and EntityFramework Core packages

```sh
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package AutoMapper

```

# Sample Code

```C#

public class Customer
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public int CustomerId { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }

    public string Address { get; set; }
}

public class CustomerResponse
 {
     public int CustomerId { get; set; }
     public string FirstName { get; set; }
     public string LastName { get; set; }
 }


try
{
    await _customerService.CreateCustomerAsync(customer);
    var customerResponse = _mapper.Map<CustomerResponse>(customer);

    var uri = "api/v1/customers/" + customer.CustomerId;
    return Created(uri, customerResponse);
}
catch (Exception ex)
{
    return null;
}           



 public MappingProfile()
 {
     CreateMap<Customer, CustomerResponse>();

 }

```
