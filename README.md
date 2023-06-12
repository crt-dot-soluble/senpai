# Senpai Language & AI Interpreter - Formal Standard

This document outlines the formal standards for the Senpai language and the corresponding AI Interpreter. It describes the syntax and features of the Senpai language and provides examples for each feature. The document also lays down the formal standard for the AI interpreter that translates Senpai files into CSharp source code.

## Senpai Language

The Senpai language, designated by the file extension `.senpai`, is designed to outline class structures, interfaces, and objects in a simplified format. Its aim is to increase readability and ease of writing for developers. Here's the standard syntax for various Senpai language features:

### Classes

Syntax:
```toml
[class.ClassName]
access = "access_modifier"
extends = "BaseClassName"
attributes = ["access_modifier type attribute_name"]
methods = ["access_modifier return_type method_name(args)"]
```
Example:
```toml
[class.Person]
access = "public"
extends = ""
attributes = ["private string name", "private int age"]
methods = ["public void Speak(string words)", "private int CalculateAge(int birthYear)"]
```

### Structs

Syntax:
```toml
[struct.StructName]
access = "access_modifier"
attributes = ["access_modifier type attribute_name"]
```
Example:
```toml
[struct.Color]
access = "public"
attributes = ["public float r", "public float g", "public float b"]
```

### Interfaces

Syntax:
```toml
[interface.InterfaceName]
access = "access_modifier"
methods = ["return_type method_name(args)"]
```
Example:
```toml
[interface.IRunnable]
access = "public"
methods = ["void Run()"]
```

### Inheritance and Overriding

A class can inherit from a base class using the `extends` keyword. Method overriding is indicated with `override` in the method declaration.

Example:
```toml
[class.Dog]
access = "public"
extends = "Animal"
attributes = ["private string breed"]
methods = ["public void Bark()", "override public void Eat()"]
```

## Senpai AI Interpreter

The Senpai AI Interpreter is responsible for translating Senpai language files into idiomatic, well-structured CSharp source code, following the most recent Microsoft CSharp and .NET Core standards. The Interpreter adheres to the following standards:

1. **Language and Format**: The AI processes `.senpai` files and outputs source code files in CSharp.
2. **Coding Standards**: The AI generates code conforming to the latest CSharp and .NET Core standards and conventions as defined by Microsoft.
3. **Library Use**: The AI generates code that uses only vanilla CSharp and .NET Core, and doesn't rely on external packages or libraries.
4. **Code Reusability**: If a function is defined in the Senpai pseudo code and is beneficial in a new context, the AI reuses this function in the generated code.
5. **Code Clarity**: The AI generates code in a declarative style, making it as self-explanatory as possible to reduce the need for extensive comments.
6. **Pre-Compilation Analysis**: Before generating any CSharp code, the AI analyzes the entire Senpai pseudo code and logs any detected issues in a logically formatted markdown document, each with a proposed solution.
7. **File Structure and Code Generation**: If no issues are found in the pseudo code, the AI presents the file structure in a graphical manner, followed by the corresponding generated CSharp code.
8. **Documentation**: All generated code includes complete inline documentation, following CSharp XML comments standards.
9. **Source Attribution**: The first line of every generated source file is `// -- Generated From Senpai`, followed by two line breaks,

 to clearly mark the source of the code.

## Examples

Here are examples showcasing the generation of code with multiple Senpai language features:

1. **Generating a Simple Class:**
   - Senpai Code:
     ```toml
     [class.Person]
     access = "public"
     attributes = ["private string name", "private int age"]
     methods = ["public void Speak(string words)", "private int CalculateAge(int birthYear)"]
     ```
   - Generated CSharp Code:
     ```csharp
     // -- Generated From Senpai
     
     public class Person
     {
         private string name;
         private int age;
         
         public void Speak(string words)
         {
         }
         
         private int CalculateAge(int birthYear)
         {
         }
     }
     ```

2. **Generating an Interface and Implementing Class:**
   - Senpai Code:
     ```toml
     [interface.IRunnable]
     access = "public"
     methods = ["void Run()"]
     
     [class.Dog]
     access = "public"
     extends = "Animal"
     implements = ["IRunnable"]
     attributes = ["private string breed"]
     methods = ["public void Bark()", "override public void Eat()", "public void Run()"]
     ```
   - Generated CSharp Code:
     ```csharp
     // -- Generated From Senpai
     
     public interface IRunnable
     {
         void Run();
     }
     
     public class Dog : Animal, IRunnable
     {
         private string breed;
         
         public void Bark()
         {
         }
         
         public override void Eat()
         {
         }
         
         public void Run()
         {
         }
     }
     ```

3. **Generating a Struct:**
   - Senpai Code:
     ```toml
     [struct.Color]
     access = "public"
     attributes = ["public float r", "public float g", "public float b"]
     ```
   - Generated CSharp Code:
     ```csharp
     // -- Generated From Senpai
     
     public struct Color
     {
         public float r;
         public float g;
         public float b;
     }
     ```

Please use these examples as a guide when writing Senpai code.
