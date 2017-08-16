# C# Style Guide

This style guide is different from other you may see, because the focus is
centered on readability for print and the web. We created this style guide to
keep the code in our tutorials consistent.  

Our overarching goals are **conciseness**, **readability** and **simplicity**. Also, this guide is written to keep **Unity** in mind. 

## Inspiration

This style guide is based on C# and Unity conventions. 

## Table of Contents

- [Tools](#tools)
- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Parameters](#parameters--parameters)
  + [Delegates](#delegates--delegates)
  + [Events](#events--events)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Class Definition Order](#class-definition-order)
  + [Interfaces](#interfaces)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Brace Style](#brace-style)
- [Performace Consideration](#performace-consideration)
- [Switch Statements](#switch-statements)
- [Unit tests and functional tests](#unit-tests-and-functional-tests)
  + [Assembly naming](#assembly-naming)
  + [Unit test class naming](#unit-test-class-naming)
  + [Unit test method naming](#unit-test-method-naming)
  + [Unit test structure](#unit-test-structure)
  + [Testing exception messages](#testing-exception-messages)
  + [Use xUnit.net's plethora of built-in assertions](#use-xunitnets-plethora-of-built-in-assertions)
  + [Parallel tests](#parallel-tests)
- [Language](#language)
- [Copyright Statement](#copyright-statement)
- [Smiley Face](#smiley-face)
- [Credit](#credits)

## Tools

- [ReSharper](http://www.jetbrains.com/resharper/) is a useful third-party code cleanup and style tool.
- [StyleCop](http://stylecop.codeplex.com/) analyzes C# source code to enforce a set of style and consistency rules and has been integrated into many third-party development tools such as ReSharper.
- [FxCop](http://codebox/SDLFxCop) is an application that analyzes managed code assemblies (code that targets the .NET Framework common language runtime) and reports information about the assemblies, such as possible design, localization, performance, and security improvements.

## Nomenclature

On the whole, naming should follow C# standards.

### Namespaces

Namespaces are all **PascalCase**, multiple words concatenated together, without hypens ( - ) or underscores ( \_ ):

**BAD**:

```csharp
com.raywenderlich.fpsgame.hud.healthbar
```

**GOOD**:

```csharp
RayWenderlich.FPSGame.HUD.Healthbar
```

### Classes & Interfaces

Written in **PascalCase**. For example `RadialSlider`. 

### Methods

Methods are written in **PascalCase**. For example `DoSomething()`. 

### Fields

All non-static fields are written **camelCase**. Per Unity convention, this includes **public fields** as well.

For example:

```csharp
public class MyClass 
{
    public int publicField;
    int packagePrivate;
    private int myPrivate;
    protected int myProtected;
}
```

**BAD:**

```csharp
private int _myPrivateVariable
```

**GOOD:**

```csharp
private int myPrivateVariable
```

Static fields are the exception and should be written in **PascalCase**:

```csharp
public static int TheAnswer = 42;
```

### Parameters

Parameters are written in **camelCase**.

**BAD:**

```csharp
void DoSomething(Vector3 Location)
```
**GOOD:**

```csharp
void DoSomething(Vector3 location)
```

Single character values are to be avoided except for temporary looping variables.

### Delegates

Delegates are written in **PascalCase**.

When declaring delegates, DO add the suffix **EventHandler** to names of delegates that are used in events. 

**BAD:**

```csharp
public delegate void Click()
```
**GOOD:**

```csharp
public delegate void ClickEventHandler()
```  

DO add the suffix **Callback** to names of delegates other than those used as event handlers.

**BAD:**

```csharp
public delegate void Render()
```
**GOOD:**

```csharp
public delegate void RenderCallback()
```  

### Events

Prefix event methods with the prefix **On**.

**BAD:**

```csharp
public static event CloseCallback Close;
```  

**GOOD:**

```csharp
public static event CloseCallback OnClose;
```

### Misc

In code, acronyms should be treated as words. For example:

**BAD:**

```csharp
XMLHTTPRequest
String URL
findPostByID
```  

**GOOD:**

```csharp
XmlHttpRequest
String url
findPostById
```

## Declarations

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

**BAD:**

```csharp
string username, twitterHandle;
```

**GOOD:**

```csharp
string username;
string twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Class Definition Order

The class definition contains class members in the following order, from less restricted scope (public) to more restrictive (private):

- ~~Nested types, e.g. classes, enum, struct, etc.~~ Non-private nested types are not allowed.
- Field members (for example, member variables, const, etc.)
- Member functions
  - Constructors
  - Finalizer (Do not use unless absolutely necessary)
  - Methods (Properties, Events, Operations, Overridables and Static)
  - Private nested types

### Interfaces

All interfaces should be prefaced with the letter **I**. 

**BAD:**

```csharp
RadialSlider
```

**GOOD:**

```csharp
IRadialSlider
```

## Spacing

Spacing is especially important in raywenderlich.com code, as code needs to be easily readable as part of the tutorial. 

### Indentation

Indentation should be done using **spaces** â€” never tabs.  

#### Blocks

Indentation for blocks uses **4 spaces** for optimal readability:

**BAD:**

```csharp
for (int i = 0; i < 10; i++) 
{
  Debug.Log("index=" + i);
}
```

**GOOD:**

```csharp
for (int i = 0; i < 10; i++) 
{
    Debug.Log("index=" + i);
}
```

#### Line Wraps

Indentation for line wraps should use **4 spaces** (not the default 8):

**BAD:**

```csharp
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

**GOOD:**

```csharp
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Line Length

Lines should be no longer than **100** characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.


## Brace Style

All braces get their own line as it is a C# convention:

**BAD:**

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**GOOD:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

**BAD:**

```csharp
if (someTest)
    doSomething();  

if (someTest) doSomethingElse();
```

**GOOD:**

```csharp
if (someTest) 
{
    DoSomething();
}  

if (someTest)
{
    DoSomethingElse();
}
```

## Performace Consideration
- **DO** use `sealed` for private classes if they are not to be inherited.
- **DO** add `readonly` to fields if they do not tend to be changed.
- **DO** use `static` methods if it is not instance relevant.
- **DO** use `RegexOptions.Compiled` for `readonly Regex`.


## Switch Statements

Switch-statements come with `default` case by default (heh). When your code is written correctly, it should never reach this part.
Never include the `default` case.

**BAD:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
    default:
        break;
}
```

**GOOD:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
}
```

## Unit tests and functional tests

#### Assembly naming

The unit tests for the `Microsoft.Foo` assembly live in the
`Microsoft.Foo.Tests` assembly.

The functional tests for the `Microsoft.Foo` assembly live in the
`Microsoft.Foo.FunctionalTests` assembly.

In general there should be exactly one unit tests assembly for each
product runtime assembly. In general there should be one functional
tests assembly per repo. Exceptions can be made for both.

#### Unit test class naming

Test class names end with `Test` suffix and live in the same namespace
as the class being tested. For example, the unit tests for the
`Microsoft.Foo.Boo` class would be in a `Microsoft.Foo.BooTest` class in
the unit tests assembly `Microsoft.Foo.Tests`.

#### Unit test method naming

Unit test method names must be descriptive about *what developers are
testing, under what conditions, and what the expectations are*. Pascal
casing and underscores can be used to improve readability. The following
test names are correct:

```csharp
PublicApiArgumentsShouldHaveNotNullAnnotation
Public_api_arguments_should_have_not_null_annotation
```

The following test names are incorrect:

```csharp
Test1
Constructor
FormatString
GetData
```

#### Unit test structure

The contents of every unit test should be split into three distinct
stages (arrange, act and assert), optionally separated by these
comments:

```csharp
// Arrange
// Act
// Assert
```

The crucial thing here is the `Act` stage is exactly one statement. That
one statement calls only the one method that you are trying to test.
Keeping that one statement as simple as possible is also very important.
For example, this is not ideal:

```csharp
int result = myObj.CallSomeMethod(GetComplexParam1(), GetComplexParam2(), GetComplexParam3());
```

This style is not recommended because too much can go wrong in this one
statement. All the `GetComplexParamN()` calls can throw exceptions for a
variety of reasons unrelated to the test itself. It is thus unclear to
someone running into a problem why the failure occurred.

The ideal pattern is to move the complex parameter building into the
`Arrange` section:

```csharp
// Arrange
P1 p1 = GetComplexParam1();
P2 p2 = GetComplexParam2();
P3 p3 = GetComplexParam3();

// Act
int result = myObj.CallSomeMethod(p1, p2, p3);

// Assert
Assert.AreEqual(1234, result);
```

Now the only reason the line with `CallSomeMethod()` can fail is if the
method itself throws an error.

#### Testing exception messages

Testing the specific exception message in a unit test is important. This
ensures that the desired exception is being tested rather than a
different exception of the same type. In order to verify the exact
exception, it is important to verify the message.

```csharp
// Act
var ex = Assert.Throws<InvalidOperationException>(() => fruitBasket.GetBananaById(-1));

// Assert
Assert.Equal("Cannot load banana with negative identifier.", ex.Message);
```

#### Use xUnit.net's plethora of built-in assertions {#use-xunitnets-plethora-of-built-in-assertions}

xUnit.net includes many kinds of assertions – please use the most
appropriate one for your test. This makes the tests much more readable
and also allows the test runner to report the best possible errors
(whether it's local or the CI machine). For example, these are bad:

```csharp
Assert.Equal(true, someBool);

Assert.True("abc123" == someString);

Assert.True(list1.Length == list2.Length);

for (int i = 0; i < list1.Length; i++) {
    Assert.True(
        String.Equals(
            list1[i],
            list2[i],
            StringComparison.OrdinalIgnoreCase));
}
```

These are good:

```csharp
Assert.True(someBool);

Assert.Equal("abc123", someString);

// built-in collection assertions!
Assert.Equal(list1, list2, StringComparer.OrdinalIgnoreCase);
```

#### Parallel tests

By default all unit test assemblies should run in parallel mode, which
is the default. Unit tests shouldn't depend on any shared state, and so
should generally be runnable in parallel. If tests fail in parallel, the
first thing to do is to figure out why; do not just disable parallel
testing!

For functional tests, you can disable parallel tests.


## Language

Use US English spelling.

**BAD:**

```csharp
string colour = "red";
```

**GOOD:**

```csharp
string color = "red";
```

The exception here is `MonoBehaviour` as that's what the class is actually called.

## Copyright Statement

The following copyright statement should be included at the top of every source file:

    /*
     * Copyright (c) 2017 Razeware LLC
     * 
     * Permission is hereby granted, free of charge, to any person obtaining a copy
     * of this software and associated documentation files (the "Software"), to deal
     * in the Software without restriction, including without limitation the rights
     * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
     * copies of the Software, and to permit persons to whom the Software is
     * furnished to do so, subject to the following conditions:
     * 
     * The above copyright notice and this permission notice shall be included in
     * all copies or substantial portions of the Software.
     *
     * Notwithstanding the foregoing, you may not use, copy, modify, merge, publish, 
     * distribute, sublicense, create a derivative work, and/or sell copies of the 
     * Software in any work that is designed, intended, or marketed for pedagogical or 
     * instructional purposes related to programming, coding, application development, 
     * or information technology.  Permission for such use, copying, modification,
     * merger, publication, distribution, sublicensing, creation of derivative works, 
     * or sale is expressly withheld.
     *    
     * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
     * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
     * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
     * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
     * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
     * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
     * THE SOFTWARE.
     */

## Smiley Face

Smiley faces are a very prominent style feature of the raywenderlich.com site!
It is very important to have the correct smile signifying the immense amount of happiness and excitement for the coding topic. The closing square bracket ] is used because it represents the largest smile able to be captured using ASCII art. A closing parenthesis ("**:)**") creates a half-hearted smile, and thus is not preferred.

**BAD**:

:)

**GOOD**:

:]  
  
>> **NOTE**: Do not use smileys in your scripts.

## Credits

This style guide is a collaborative effort from the most stylish
raywenderlich.com team members:

- [Darryl Bayliss](https://github.com/DarrylBayliss)
- [Sam Davies](https://github.com/sammyd)
- [Mic Pringle](https://github.com/micpringle)
- [Brian Moakley](https://github.com/VegetarianZombie)
- [Ray Wenderlich](https://github.com/rwenderlich)
- [Eric Van de Kerckhove](https://github.com/BlackDragonBE)

