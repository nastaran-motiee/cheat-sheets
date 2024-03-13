- [C# Language Reference Link](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/)

- A **variable** name is a human-friendly label that the compiler assigns to a memory address. When you want to store or change a value in that memory address, or whenever you want to retrieve the stored value, you just use the variable name you created.


- An **escape character sequence** s is an instruction to the runtime to insert a special character that will affect the output of your string. In C#, the escape character sequence begins with a backslash \ followed by the character you're escaping. For example, the `\n` sequence will add a new line, and a `\t` sequence will add a tab.
`\u` followed by four hexadecimal digits represents a Unicode character. For example, `\u0041` is the Unicode escape sequence for the uppercase letter A.

  > [!NOTE] 
  > The `\u` escape secuence not always works in all environments. It is possible that the user's console doesn't support Unicode characters. In that case, the message is only displayed as question mark characters. 


- A **verbatim string literal** will keep all whitespace and characters without the need to escape the backslash. To create a verbatim string, use the `@` directive before the literal string.

  For example:
  ```csharp
  Console.WriteLine(@"c:\source\repos    
        (this is where your code goes)");
  ```
  
- **Interpolated string structure**: `$"any string {variable} any string"`;

- **Verbatim literals** and **String interpolation** can be combined.
  
  For example:
  ```csharp
  string filePath = $@"C:\Users\username\Documents\";
  ```

-  The reuse of one symbol for multiple purposes is sometimes called **overloading the operator** and happens frequently in C#. For example, the `+` symbol is used for both addition and string concatenation.
   - When it can, the C# compiler will implicitly convert an `int` into a `string` if it's obvious that the developer is trying to concatenate the string representation of a number for presentation purposes.
   - Use parentheses to define an order of operations to explicitly tell the compiler that you want to perform certain operations before other operations.

- **Order of operations** in C# is the same as in algebra. The order of operations is:
In math, PEMDAS is an acronym that helps students remember the order of operations. The order is:

  1. Parentheses (whatever is inside the parenthesis is performed first)
  1. Exponents
  1. Multiplication and Division (from left to right)
  1. Addition and Subtraction (from left to right)

  C# follows the same order as PEMDAS except for exponents. While there's no exponent operator in C#, you can use the [System.Math.Pow](https://learn.microsoft.com/en-us/dotnet/api/system.math.pow?view=net-8.0) method. The module "Call methods from the .NET Class Library using C#" will feature this method and others.

- The division of two int values will result in the truncation of any values after the decimal point. 
- To retain values after the decimal point, you need to cast the divisor or dividend (or both) from int into a floating point number like decimal first, then the quotient must be of the same floating point type as well in order to avoid truncation.

- **Tab stop locations** are set at four-character intervals, and each tab will advance to the next tab stop location. If you have a string of five characters followed by a tab escape sequence, the escape sequence will advance to the tab stop at the eight-character location, filling the gap with space characters to create whitespace in the output. However, you can advance to the same location if you have a string of seven characters followed by a tab escape sequence. This makes tab escape sequences more noticeable when they occur further from the next tab stop location.

- **.NET** is a cross-platform, open-source developer platform that can be used to develop different types of applications. It includes the software languages and code libraries used to develop .NET applications. You can write .NET applications in C#, F#, or Visual Basic.

  The .NET runtime is the code library that's required to run your C# applications. You may also see the .NET runtime referred to as the Common Language Runtime, or CLR. The .NET runtime isn't required to write your code, but it's required to actually run your applications.

- At the Terminal command prompt, to create a new console application in a specified folder, enter the following command:
  
  ```.NET CLI
  dotnet new console -o ./CsharpProjects/TestProject
  ```

    This .NET CLI command uses a .NET program template to create a new C# console application project in the specified folder location. The command creates the CsharpProjects and TestProject folders for you, and uses TestProject as the name of your .csproj file.

  In the EXPLORER panel, expand the CsharpProjects folder.

  You should see the TestProject folder and two files, a C# program file named Program.cs and a C# project file named TestProject.csproj. The CLI command uses the folder name when it creates the project file (TestProject.csproj). The Program.cs file is the file containing your C# code.

- To compile a build of your application, enter the following command at the Terminal command prompt:

  ```.NET CLI
   dotnet build
   ```


  The `dotnet build` command builds the project and its dependencies into a set of binaries. The binaries include the project's code in Intermediate Language (IL) files with a .dll extension. Depending on the project type and settings, other files may also be included. If you're curious, you can find the TestProject.dll file in the EXPLORER panel at a folder location that's similar to the following path:

  `C:\Users\someuser\Desktop\CsharpProjects\TestProject\bin\Debug\net7.0\`

  > [!NOTE]
  > Your folder path will reflect your account and the folder path to your TestProject folder.

- To run your application, enter the following command at the Terminal command prompt:

  ```.NET CLI
  dotnet run
  ```
  The `dotnet run` command runs source code without any explicit compile or launch commands. It provides a convenient option to run your application from the source code with one command. It's useful for fast iterative development from the command line. The command depends on the dotnet build command to build the code.

- **.NET Runtime**,  hosts and manages your code as it executes on the end user's computer. 
  
- **.NET Class Library**, a prewritten collection of coding resources that you can use in your applications.

# System Namespace
Contains fundamental classes and base classes that define commonly-used value and reference data types, events and event handlers, interfaces, attributes, and processing exceptions.

### Console Class

| Methods       | Description                                          |
| ------------- | ---------------------------------------------------- |
| `Write()`     |                                                      |
| `WriteLine()` |                                                      |
| `ReadLine()`  | Used to collect user input in a console application. |


# Literal Values
A **literal** is literally a hard-coded value.

| Type           | Example         |
| -------------- | --------------- |
| Integer        | 42              |
| Floating-point | 3.14            |
| String         | "Hello, World!" |
| Boolean        | true            |
| Character      | 'A'             |
| Null           | null            |


| Float Type | Precision     | Literal Suffix |
| ---------- | ------------- | -------------- |
| float      | ~6-9 digits   | `f` or `F`     |
| double     | ~15-17 digits |
| decimal    | 28-29 digits  | `m` or `M`     |


# Creating an instance of a class
```csharp
ClassName objectName = new ClassName();
```
The new operator does several important things:

- It first requests an address in the computer's memory large enough to store a new object based on the Random class.
- It creates the new object, and stores it at the memory address.
-It returns the memory address so that it can be saved in the dice variable.

From that point on, when the dice variable is referenced, the .NET Runtime performs a lookup behind the scenes to give the illusion that you're working directly with the object itself.

The latest version of the .NET Runtime enables you to instantiate an object without having to repeat the type name (target-typed constructor invocation). For example, the following code will create a new instance of the Random class:

```csharp
Random dice = new();
```

The intention is to simplify code readability. You always use parentheses when writing a target-typed new expression.

> [!NOTE]
> Often times, the terms 'parameter' and 'argument' are used interchangeably. However, 'parameter' refers to the variable that's being used inside the method. An 'argument' is the value that's passed when the method is called.

- Overloaded methods support several implementations of the method, each with a unique method signature (the number of input parameters and the data type of each input parameter).


# using statement 
The `using` statement, ensures the correct use of disposable objects.

for example:
```csharp
using System;
```
Here the `using` statement enables you to write code that implements members of the` System` namespace without requiring you to specify System. For example, your code can use the `Console.WriteLine()` method without having to specify `System.Console.WriteLine()`. Among other things, the `using` statement makes your code easier to read.


# String Methods
| Method         | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `ToUpper()`    | Converts a string to uppercase.                                |
| `ToLower()`    | Converts a string to lowercase.                                |
| `Trim()`       | Removes leading and trailing white space.                      |
| Contains()     | Returns true if a specified string is found within the string. |
| `StartsWith()` | Returns true if the string starts with a specified string.     |
| `EndsWith()`   | Returns true if the string ends with a specified string.       |
