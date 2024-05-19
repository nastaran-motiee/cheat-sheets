# .NET & C#

### General Terms
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

- **MVP (Minimal Viable Product)** - is a feature intended to be a simple working prototype of a feature that enables quick and easy delivery. A MVP is not usually a final product, it is intended to help you work through an idea, test it, and gather further requirements.

- **Scope Creep** - Some developers refer to the addition of requirements during development as ___"scope creep"___. Even if combining the new required features does not require much work, it still adds time and complexity. For this reason, you should let the team know that added requirements will likely delay the completion of the project.
-  We can use paretheses to create multiple conditions using conditional (ternary) operator. **For Example:** `stringfortune = (luck > 75 ? good : (luck < 25 ? bad : neutral));`

#
<h4 style="color:#E62E29">Creating and using Methods in C#</h4>

- **In C#, a method can be called before or after its definition.** It's common to define all methods at the end of a program. When you call a method, the code in the method body will be executed. This means execution control is passed from the method caller to the method. Control is returned to the caller after the method completes its execution. Method names should be Pascal case and generally shouldn't start with digits. 
- **Falsy value** is any value that, if cast to bool, becomes false.
- Variables can be categorized as value types and reference types.
- Value types directly contain values, and reference types store the address of the value.
- Methods using value type arguments create their own copy of the values.
- Methods that perform changes on an array parameter affect the original input array.
- String is an immutable reference type.
- Methods that perform changes on a string parameter don't affect the original string.
-  **Scope** is a term that's talking about variable lifetime,and how long these variables actually exist.
-  **The C Sharp language allows the use of named and optional parameters**. These types of parameters let you select which arguments you want to supply to the method, so you aren't restricted to the structure defined in the method signature.
- **Named arguments** allow you to specify the value for a parameter using its name rather than position. 
- **Optional parameters** allow you to omit those arguments when calling the method.
-  It isn't necessary to name all of the arguments. For example, the following syntax is also valid: <br/> `RSVP("Linh", 2, allergies: "none", inviteOnly: false);` <br/>`RSVP("Linh", partySize: 2, "none", false);`
- Named arguments are also valid as long as they're not followed by any positional arguments. For example, including "Linh" and 2 at the end would be invalid:<br/> <br/>
`RSVP(allergies: "none", inviteOnly: false, "Linh", 2);`<br/><br/>  Notice that the named arguments don't have to appear in the original order. However, the unnamed argument Tony is a positional argument, and must appear in the matching position.
- A parameter becomes optional when it's assigned a default value. If an optional parameter is omitted from the arguments, the default value is used when the method executes. <br/> For Example: <br/> `void RSVP(string name, int partySize = 1, string allergies = "none", bool inviteOnly = true);`

#
<h4 style="color:#E62E29">Casting in C#</h4>
 Implicit casting is only available when there's no data loss occurring as a result of the conversion.

 **For Example:**
 If you omit the cast from the return result of the following method , you'll see the following error:

_Cannot implicitly convert type 'double' to 'int'._

 ```csharp
 int UsdToVnd(double usd) 
{
    int rate = 23500;
    return (int) (rate * usd);
}
```

This happens because the compiler attempts to cast the value returned to match the data type specified in the method signature. However, implicit casting is only available when there's no data loss occurring as a result of the conversion. 

But in the following example:
```csharp
doubleVndToUsd(int vnd) 
{
    double rate = 23500;
    return vnd / rate;
}
```
you need rate to be a double or else the compiler uses integer division and return a truncated int value. USD needs to be represented by a decimal number.

If you set rate to an int instead of double, you'll notice that the compiler doesn't present you with any errors. This happens because the value of `vnd / rate` is implicitly casted to the double data type specified in the method signature. 
When creating methods that return numeric values, it's important to consider the data types in the operations your method performs.


## .NET Commands

```
dotnet new webapi -o MyMicroservice --no-https
cd MyMicroservice
```

### What do these commands mean?

The `dotnet` command creates a new application of type `webapi` (that's a REST API endpoint).

- The `-o` parameter creates a directory named `MyMicroservice` where your app is stored.
- The ``--no-https`` flag creates an app that will run without an HTTPS certificate, to keep things simple for deployment.

The `cd MyMicroservice` command puts you into the newly created app directory.

### The generated code
Several files were created in the MyMicroservice directory, to give you a simple service that is ready to run, including the following files:

- `Program.cs` is the entry point file and contains all the settings and configuration that are loaded when the app starts and has code for a simple API that returns the weather forecast for the next five days. It also starts the application.
- `MyMycroservice.http` is used for testing ASP.NET Core projects.
- `MyMicroservice.csproj` defines the version of .NET the app is targeting, what libraries the project references, etc.
- The `launchSettings.json`file inside the `Properties` directory defines different profile settings for the local development environment. A port number ranging between 5000-5300 is automatically assigned at project creation and saved on this file.
- [C# Language Reference Link](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/)


## System Namespace
Contains fundamental classes and base classes that define commonly-used value and reference data types, events and event handlers, interfaces, attributes, and processing exceptions.

### Console Class Methods

| Methods       | Description                                                                                                                |
| ------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `Write()`     |                                                                                                                            |
| `WriteLine()` |                                                                                                                            |
| `ReadLine()`  | Used to collect user input in a console application.                                                                       |
| `Clear()`     | Clears the console window.          <br/> **NOTE:** the` Console.Clear` method is throwing an exception in debug sessions. |




## Literal Values
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


## Creating an instance of a class
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


## using statement 
The `using` statement, ensures the correct use of disposable objects.

for example:
```csharp
using System;
```
Here the `using` statement enables you to write code that implements members of the` System` namespace without requiring you to specify System. For example, your code can use the `Console.WriteLine()` method without having to specify `System.Console.WriteLine()`. Among other things, the `using` statement makes your code easier to read.


## String Methods
| Method          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Contains()`    | Returns true if a specified string is found within the string.                                                                                                                                                                                                                                                                                                                                                                                                |
| `EndsWith()`    | Returns true if the string ends with a specified string.                                                                                                                                                                                                                                                                                                                                                                                                      |
| `Format()`      | Replaces one or more format items in a specified string with the string representation of a specified object.                                                                                                                                                                                                                                                                                                                                                 |
| `IndexOf()`     | Returns the first position of a `char` or `string` inside of another string.                                                                                                                                                                                                                                                                                                                                                                                  |
| `IndexOfAny() ` | Returns the first position of an array of `char` that occurs inside of another string.                                                                                                                                                                                                                                                                                                                                                                        |
| `Join()`        | Concatenates the elements of a specified array or the members of a collection, using the specified separator between each element or member.<br/>**For Example:** `string result = String.Join(",", valueArray);`                                                                                                                                                                                                                                             |
| `LastIndexOf()` | Returns the last position of a character or string inside of another string.                                                                                                                                                                                                                                                                                                                                                                                  |
| `Remove()`      | Returns a new string in which a specified number of characters from the current string are deleted.     <br/> You would typically use `Remove()` when there's a standard and consistent position of the characters you want to remove from the string.                                                                                                                                                                                                        |
| `Replace()`     | The `Replace()` method is used when you need to replace one or more characters with a different character (or no character). <br/>The `Replace()` method is different from the other methods used so far, it replaces every instance of the given characters, not just the first or last instance.                                                                                                                                                            |
| `StartsWith()`  | Returns true if the string starts with a specified string.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `Split()`       | Splits a string into substrings based on the characters in an array. <br/>**Example 1:** <br/>`string[] values = readResult.Split(',');` <br/><br/> **Example 2:** <br/> In this example, using StringSplitOptions.RemoveEmptyEntries omits empty entries from the address array and prevent attempts to parse empty strings.            <br/>                              `string[] address = ipv4Input.Split(".", StringSplitOptions.RemoveEmptyEntries);` |
| `Substring()`   | Retrieves a substring from this instance. The substring starts at a specified character position and has a specified length.                                                                                                                                                                                                                                                                                                                                  |
| `ToUpper()`     | Converts a string to uppercase.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `ToLower()`     | Converts a string to lowercase.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `Trim()`        | Removes leading and trailing white space.                                                                                                                                                                                                                                                                                                                                                                                                                     |

##### Resources
- [String Class](https://learn.microsoft.com/en-us/dotnet/api/system.string?view=net-8.0)
- [String.Format Method](https://learn.microsoft.com/en-us/dotnet/api/system.string.format?view=net-7.0&preserve-view=true)
- [Standard Numeric Format Strings](https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings)

## Nullable Types
A nullable value type `T?` represents all values of its underlying value type `T` and an additional null value. For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`. An underlying value type `T` cannot be a nullable value type itself.

The following code shows how to declare a nullable type:

```csharp
int? num = null;

```
>[!NOTE]
> When reading user entered values with the Console.ReadLine() method, it's best to enable a nullable type string using string? to avoid the code compiler generating a warning when you build the project.

> [!NOTE]
> If you want to use `Console.ReadLine()` input for numeric values, you need to convert the string value to a numeric type.
> The `int.TryParse()` method can be used to convert a string value to an integer. The method uses two parameters, a string that will be evaluated and the name of an integer variable that will be assigned a value. The method returns a Boolean value. The following code sample demonstrates using the `int.TryParse()` method:


```csharp
// capture user input in a string variable named readResult
int numericValue = 0;
bool validNumber = false;

validNumber = int.TryParse(readResult, out numericValue);
```
> If the string value assigned to `readResult` represents a valid integer, the value will be assigned to the integer variable named `numericValue`, and `true` will be assigned to the Boolean variable named `validNumber`. If the value assigned to `readResult` doesn't represent a valid integer, `validNumber` will be assigned a value of `false`. For example, if `readResult` is equal to "7", the value `7` will be assigned to `numericValue`.


## Jagged Arrays vs Multidimensional Arrays
In a multidimensional array, each element in each dimension has the same, fixed size as the other elements in that dimension. In a jagged array, which is an array of arrays, each inner array can be of a different size.
In addittion, each element contained within the array is a separate item of the array type.

**Example:**
```csharp
public class ArrayHolder
{
    int[][] jaggedArray = { new int[] {1,2,3,4},
                            new int[] {5,6,7},
                            new int[] {8},
                            new int[] {9}
                          };

    int[,] multiDimArray = {{1,2,3,4},
                             {5,6,7,0},
                             {8,0,0,0},
                             {9,0,0,0}
                            };
}
```
**Example:**
```csharp
//multidimensional array
string [,] twoDimensionalArray = new string[3,3];
```
> [!NOTE]
> In a multidimentional array the `foreach` statement wouldn't process the two array dimensions separately. 
> For in a n x m array, the `foreach` statement would process the n x m elements in a single dimension. 
> However, if the array was a jagged array configured as an array of arrays In this case, you would create a `foreach` for an outer loop and second `foreach` for an inner loop. The outer loop would iterate through the array elements in the jagged array. 


## int32 Methods
Used like: `int.MethodName();`
| Method                                | Description                                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `TryParse(string? s, out int result)` | Converts the string `s` to to an integer `result` if possible and returns `true`, else returns `false` |


## What is data?
Answering the question "what is data" depends on who you ask, and in what context you're asking it.

In software development, data is essentially a value that is stored in the computer's memory as a series of bits. A bit is a simple binary switch represented as a 0 or 1, or rather, "off" and "on." A single bit doesn't seem useful, however when you combine 8 bits together in a sequence, they form a byte. When used in a byte, each bit takes on a meaning in the sequence. In fact, you can represent 256 different combinations with just 8 bits if you use a binary (base-2) numeral system.

For example, in a binary numeral system, you can represent the number 195 as 11000011. The following table helps you visualize how this works. The first row has eight columns that correspond to a position in a byte. Each position represents a different numeric value. The second row can store the value of an individual bit, either 0 or 1.

| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 0   | 0   | 0   | 0   | 1   | 1   |

If you add up the number from each column in the first row that corresponds to a 1 in the second row, you get the decimal equivalent to the binary numeral system representation. In this case, it would be 128 + 64 + 2 + 1 = 195.

To work with larger values beyond 255, your computer stores more bytes (commonly 32-bit or 64-bit). If you're working with millions of large numbers in a scientific setting, you may need to consider more carefully which data types you're using. Your code could require more memory to run.


## What about textual data?
If a computer only understands 0s and 1s, then how does it allow you to work with text? Using a system like ASCII (American Standard Code for Information Interchange), you can use a single byte to represent upper and lowercase letters, numbers, tab, backspace, newline and many mathematical symbols.

For example, if you wanted to store a lower-case letter a as a value in my application, the computer would only understand the binary form of that value. To better understand how a lower-case letter a is handled by the computer, I need to locate an ASCII table that provides ASCII values and their decimal equivalents. You can search for the terms "ASCII lookup decimal" to locate such a resource online.

In this case, the lower-case letter a is equivalent to the decimal value 97. Then, you would use the same binary numeral system in reverse to find how an ASCII letter a is stored by the computer.

| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   | 1   | 0   | 0   | 0   | 0   | 1   |

Since 64 + 32 + 1 = 97, the 8-bit binary ASCII code for a is 01100001.

It's likely that you'll never need to perform these types of conversions on your own, but understanding the computer's perspective of data is a foundational concept, especially as you're considering data types.

## What is a data type?
A data type is a way a programming language defines how much memory to save for a value. There are many data types in the C# language to be used for many different applications and sizes of data.

For most of the applications you build in your career, you'll settle on a small subset of all the available data types. However, it's still vital to know others exist and why.

Value vs. reference types
This module focuses on the two kinds of types in C#: reference types and value types.

Variables of reference types store references to their data (objects), that is they point to data values stored somewhere else. In comparison, variables of value types directly contain their data. 

## Simple value types
Simple value types are a set of predefined types provided by C# as keywords. These keywords are aliases (a nickname) for predefined types defined in the .NET Class Library. For example, the C# keyword `int` is an alias of a value type defined in the .NET Class Library as `System.Int32`.

Simple value types include many of the data types that you may have used already like `char` and `bool`. There are also many **integral** and **floating-point** value types to represent a wide range of whole and fractional numbers.

#### Recap
- Values are stored as bits, which are simple on / off switches. 
- Combining enough of these switches allows you to store just about any possible value.
- There are two basic categories of data types: value and reference types. The difference is in how and where the values are stored by the computer as your program executes.
- Simple value types use a keyword alias to represent formal names of types in the .NET Library.

## Array Class Methods
| Method        | Description                                                                                                                                                                                                                                                      | Explenation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear()`     | To remove the contents of specific elements in your array and replace it with the array default value. For example, in a string array the element value cleared is replaced with null, when you clear a int array element the replacement is done with 0 (zero). | **For Example:** `Array.Clear(pallets, 0, 2);` clears the values stored in the elements of the pallets array starting at index 0 and clearing 2 elements.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `GetLength()` | Returns the number of elements in the specified dimension of the array.                                                                                                                                                                                          | **For Example:** `int length = pallets.GetLength(0);` <br/> Here, we're calling the `GetLength()` method on the pallets array to get the number of elements in the first dimension of the array.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `Reverse()`   | Reverses the order of the array elements.                                                                                                                                                                                                                        |
| `Resize()`    | Adds or removes elements from your array.                                                                                                                                                                                                                        | **For Example:** `Array.Resize(ref pallets, 6);` <br/> Here, we're calling the `Resize()` method passing in the pallets array by reference, using the `ref` keyword. In some cases, methods require you pass arguments by value (the default) or by reference (using the ref keyword). The reasons why this is necessary requires a long and complicated explanation about of how objects are managed in .NET. When resizing the array to add more elements The new elements are added at the end of the current elements. The new elements will be null until you assign a value to them.When resizing the array to remove elements, the elements will be removed from the end of the array. |
| `Sort()`      | Sorts the array elements alphanumerically.                                                                                                                                                                                                                       |

## String data type's Array methods

| Method          | Description                                                                                  | Explenation |
| --------------- | -------------------------------------------------------------------------------------------- | ----------- |
| `ToCharArray()` | Creates an array of char, each element of the array has one character of the original string |


>[!NOTE]
>The expression `new string(valueArray)` creates a new empty instance of the `System.String` class (which is the same as the `string` data type in C#) and passes in the char array as a constructor.

## Composite Formatting
Composite formatting uses numbered placeholders within a string. At run time, everything inside the braces is resolved to a value that is also passed in based on their position.

**For Example:** 
``` csharp
string first = "Hello";
string second = "World";
string result = string.Format("{0} {1}!", first, second);
Console.WriteLine(result);
```

The tokens can be arranged in any order. 
For example, `{1}` before `{0}`.

Composite formatting works when using `string.Format()` or `Console.WriteLine()`.

## String interpolation
String interpolation is a technique that simplifies composite formatting.
Instead of using a numbered token and including the literal value or variable name in a list of arguments to `String.Format()`or `Console.WriteLine()`, you can just use the variable name inside of the curly braces.

**For Example:**
```csharp
string first = "Hello";
string second = "World";
Console.WriteLine($"{first} {second}!");
Console.WriteLine($"{second} {first}!");
Console.WriteLine($"{first} {first} {first}!");
```


## String Format Specifiers
A format specifier is a string of characters that defines the text representation of a value. The format specifier can be used to control the formatting of the output.



| Format Specifier                                                                                                                                                                   | Description | Notes                                                                                                                                                                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:C`                                                                                                                                                                               | Currency    | String currency formatting feature is dependent on the local computer setting for culture. In this context, the term "culture" refers to the country/region and language of the end user. Add a number afterwards to control the number of values displayed after the decimal point.                                        |
| `:N`                                                                                                                                                                               | Number      | When working with numeric data, you might want to format the number for readability by including commas to delineate thousands, millions, billions, and so on. The `N` numeric format specifier makes numbers more readable. By default, the `N` numeric format specifier displays only two digits after the decimal point. |
| If you want to display more precision, you can do that by adding a number after the specifier. For example to display four digits after the decimal point, use the `N4` specifier. |
| `:P`                                                                                                                                                                               | Percentage  | Add a number afterwards to control the number of values displayed after the decimal point.                                                                                                                                                                                                                                  |




## Combining formatting approaches
String variables can store strings created using formatting techniques. In the following example, decimals and decimal math results are formatted and stored in the your Discount string using composite formatting.
```csharp
decimal price = 67.55m;
decimal salePrice = 59.99m;

string yourDiscount = String.Format("You saved {0:C2} off the regular {1:C2} price. ", (price - salePrice), price);

Console.WriteLine(yourDiscount);
```

If you're viewing this from the en-US culture, you observe the following output.
```bash
You saved $7.56 off the regular $67.55 price. 
```


## Debugging Tools for C#

### Debugger and application interaction - Behind the scenes
A code debugger can be used to pause and resume code execution, examine variable state, and even change the values assigned to variables at runtime. You may be wondering, how can the debugger control and modify a running application? The short answer is, the debugger has access to the application's runtime environment and executable code.

The Visual Studio Code debugger for C# uses the .NET Core runtime to launch and interact with an application. When you start the debugger, it creates a new instance of the runtime and runs the application within that instance. The runtime includes an application programming interface (API), which the debugger uses to attach to the running process (your application).
Once your application is running and the debugger is attached, the debugger communicates with the running process using the .NET Core runtime's debugging APIs and a standard debug protocol. The debugger can interact with the process (the application running within the .NET runtime instance) by setting breakpoints, stepping through code, and inspecting variables. Visual Studio Code's debugger interface enables you to navigate the source code, view call stacks, and evaluate expressions.

### Debuging C# application in Visual Studio Code
Visual Studio Code uses a launch configuration file to specify the application that runs in the debug environment.

1. If the your project folder doesn't include a` ProjectName.sln` file, select `Program.cs`, and then verify that a `.sln` file is created.
Opening a C# code file prompts the environment to check for project files. The `.sln` file is a solution file that is used by Visual Studio to manage projects and is usually created automatically when you create a new project in Visual Studio Code. The `.sln` file is used by the debugger to identify the project that should be run in the debug environment.
2. On the View menu, select Command Palette.

3. At the command prompt, enter **.net: g** and then select **.NET: Generate Assets for Build and Debug**.

4. Notice the new `.vscode` folder that has been added to your project folder.The .vscode folder contains files that are used to configure the debug environment.
If you expand the `.vscode` folder, you'll see a `launch.json` file, and a `tasks.json` file.
   - The `launch.json` file, contains the launch configurations for your project.<br/>The launch configurations file can include multiple configurations. Each configuration includes a collection of attributes that are used to define that configuration. 
   - The `tasks.json` file, contains the build task for your project


### Conditional breakpoints
A conditional breakpoint is a special type of breakpoint that only triggers when a specified condition is met. For example, you can create a conditional breakpoint that pauses execution when a variable named numItems is greater than 5.

### Hit Count breakpoints and Logpoints
- A **hit count** breakpoint can be used to specify the number of times that a breakpoint must be encountered before it will "break" execution. You can specify a hit count value when creating a new breakpoint (with the Add Conditional Breakpoint action) or when modifying an existing one (with the Edit Condition action). In both cases, an inline text box with a dropdown menu opens where you can enter the hit count value.
- A **Logpoint** is a variant of a breakpoint that does not "break" into the debugger but instead logs a message to the console. Logpoints are especially useful for injecting logging while debugging production environments that cannot be paused or stopped. A Logpoint is represented by a "diamond" shaped icon rather than a filled circle. Log messages are plain text but can include expressions to be evaluated within curly braces ('{}').<br/>
Logpoints can include a conditional 'expression' and/or 'hit count' to further control when logging messages are generated. For example, you can combine a Logpoint message of `i = {i}` with Hit Count condition `>4` to generate log messagesA 'hit count' breakpoint can be used to specify the number of times that a breakpoint must be encountered before it will 'break' execution. You can specify a hit count value when creating a new breakpoint (with the Add Conditional Breakpoint action) or when modifying an existing one (with the Edit Condition action). In both cases, an inline text box with a dropdown menu opens where you can enter the hit count value.

### Debugging tips
- Use breakpoints to pause code execution during a debug session.
- Use **Step Into** from the Debug controls toolbar to observe the next executable code line.
- Use **Step Out** from the Debug controls toolbar to advance through the current method and back to the code line that called the method.



### The launch.json file
- [Examine the launch configuration file](./ExamineTheLaunchConfigurationsFileTrainingMicrosoftLearn.mhtml)