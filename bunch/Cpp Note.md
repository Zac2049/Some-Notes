# Cpp Note

## Getting started

1. Use the *debug* build configuration when developing your programs. When you’re ready to release your executable to others, or want to test performance, use the *release* build configuration.

2. Disable compiler extensions to ensure your programs (and coding practices) remain compliant with C++ standards and will work on any system.  

* <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200607144740269.png" alt="image-20200607144740269" style="zoom:33%;" />

* <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200607144853253.png" alt="image-20200607144853253" style="zoom:33%;" />

3. Turn your warning levels up to the maximum, especially while you are learning. It will help you identify possible issues.

   <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200607145045596.png" alt="image-20200607145045596" style="zoom:33%;" />

4. choosing a language standard

   <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200607145213688.png" alt="image-20200607145213688" style="zoom:33%;" />

## Basics

1. Don’t use multi-line comments inside other multi-line comments. Wrapping single-line comments inside a multi-line comment is okay.

2. Programs are collections of instructions that manipulate data to produce a desired result.

3. In general programming, the term *object* typically refers to a variable, data structure in memory, or function. In C++, the term *object* has a narrower definition that excludes functions.

4. A named object is called a **variable**, and the name of the object is called an **identifier**.

5. **Instantiation** is a fancy word that means the object will be created and assigned a memory address. Variables must be instantiated before they can be used to store values.  An instantiated object is sometimes also called an **instance**.

   keywords: **definition**, **data**, **value**, **type**, **parenthesis**, **brace**, **comma**, **cursor**, **uninitialized variable**, **keywords**, **identifier**, **curly** **braces**, **Whitespace**, **function prototype**, **naming collision** (or **naming conflict**), 

6. One downside of **assignment** is that it requires at least two statements: one to define the variable, and one to assign the value. When a variable is defined, you can also provide an initial value for the variable at the same time. This is called **initialization**.

   **copy initialization**:

   ``` c++
   int width = 5; // copy initialization of value 5 into variable width
   ```

   **direct initialization**:(recommended)

   ``` c++
   int width( 5 ); // direct initialization of value 5 into variable width
   ```

   **brace initialization**:(C++11)      **Favor direct brace initialization whenever possible.**

   ``` c++
   int width{ 5 }; // direct brace initialization of value 5 into variable width (preferred)
   int height = { 6 }; // copy brace initialization of value 6 into variable height
   ```

   **Zero initialization** generally initializes the variable to zero (or empty, if that’s more appropriate for a given type).

   ``` c++
   int width{}; // zero initialization to value 0
   ```

   Brace initialization has the added benefit of disallowing “narrowing” conversions. 

   ``` c++
   int width{ 4.5 }; // error: not all double values fit into an int
   ```

   You can initialize multiple variables defined on the same line:

   ``` c++
   int e{ 9 }, f{ 10 }; // brace initialization (preferred)
   ```

7. **std::endl vs ‘\n’**

   > Using std::endl can be a bit inefficient, as it actually does two jobs: it moves the cursor to the next line, and it “flushes” the output (makes sure that it shows up on the screen immediately). When writing text to the console using std::cout, std::cout usually flushes output anyway (and if it doesn’t, it usually doesn’t matter), so having std::endl flush is rarely important.

   > Because of this, use of the **‘\n’** character is typically **preferred** instead. The ‘\n’ character moves the cursor to the next line, but doesn’t do the redundant flush, so it performs better. The ‘\n’ character also tends to be easier to read since it’s both shorter and can be embedded into existing text.

8. **Undefined behavior** is the result of executing code whose behavior is not well defined by the C++ language，such as undefined variables.

   Code implementing undefined behavior may exhibit *any* of the following symptoms:

   - Your program produces different results every time it is run.
   - Your program consistently produces the same incorrect result.
   - Your program behaves inconsistently (sometimes produces the correct result, sometimes not).
   - Your program seems like its working but produces incorrect results later in the program.
   - Your program crashes, either immediately or later.
   - Your program works on some compilers but not others.
   - Your program works until you change some other seemingly unrelated code.
   
9. A **literal** (also known as a **literal constant**) is a fixed value that has been inserted directly into the source code.

10. An **operation** is a mathematical calculation involving zero or more input values (called **operands**) that produces a new value (called an output value). The specific operation to be performed is denoted by a construct (typically a symbol or pair of symbols) called an **operator**(**Unary**/**Binary**/**Ternary**).

11. An **expression** is a combination of literals, variables, operators, and explicit function calls (not shown above) that produce a single output value. When an expression is executed, each of the terms in the expression is evaluated until a single value remains (this process is called **evaluation**). That single value is the **result** of the expression.

12. **Nested functions are not supported**

13. The return value from `main` is sometimes called a **status code**, as it is used to indicate whether the program ran successfully or not.

    The C++ standard only defines the meaning of 3 status codes: 0, EXIT_SUCCESS, and EXIT_FAILURE. 0 and EXIT_SUCCESS both mean the program executed successfully. EXIT_FAILURE means the program did not execute successfully.

    EXIT_SUCCESS and EXIT_FAILURE are defined in the <cstdlib> header:

    ``` c++
    #include <cstdlib> // for EXIT_SUCCESS and EXIT_FAILURE
     
    int main()
    {
        return EXIT_SUCCESS;
    }
    ```

    

    If you want to maximize portability, you should only use 0 or EXIT_SUCCESS to indicate a successful termination, or EXIT_FAILURE to indicate an unsuccessful termination.

14. Always explicitly provide a return value for any function that has a non-void return type.

    Failure to return a value from a function with a non-void return type (other than main) will result in **undefined behavior.**

15. This is the essence of **modular programming**: the ability to write a function, test it, ensure that it works, and then know that we can reuse it as many times as we want and it will continue to work (so long as we don’t modify the function -- at which point we’ll have to retest it).

16. “**don’t repeat yourself**”. If you need to do something more than once, consider how to modify your code to remove as much redundancy as possible.

17. A **function parameter** is a variable used in a function. An **argument** is a value that is passed *from* the caller *to* the function when a function call is made.

    When a function is called, all of the parameters of the function are created as variables, and the value of each of the arguments is *copied* into the matching parameter. This process is called **pass by value**.

18. Function parameters, as well as variables defined inside the function body, are called **local variables**.

19. In Visual Studio, the automatic formatting options can be found under *Edit > Advanced > Format Document* and *Edit > Advanced > Format Selection*.

20. **Declarations vs. definitions**

    * A **definition** actually implements (for functions or types) or instantiates (for variables) the identifier. Here are some examples of definitions:

      ```c++
      int add(int x, int y) // implements function add()
      {
          int z{ x + y }; // instantiates variable z
       
          return z;
      }
      ```

       A definition is needed to satisfy the *linker*. If you use an identifier without providing a definition, the linker will error.

      The **one definition rule** (or ODR for short) is a well-known rule in C++. The ODR has three parts:

      1. Within a given *file*, a function, object, type, or template can only have one definition.
      2. Within a given *program*, an object or normal function can only have one definition. This distinction is made because programs can have more than one file (we’ll cover this in the next lesson).
      3. Types, templates, and inline functions and variables are allowed to have identical definitions in different files. 

      Violating part 1 of the ODR will cause the compiler to issue a redefinition error. Violating ODR part 2 will likely cause the linker to issue a redefinition error. Violating ODR part 3 will cause undefined behavior.

    * A **declaration** is a statement that tells the *compiler* about the existence of an identifier and its type information. Here are some examples of declarations

      ```c++
      int add(int x, int y); // tells the compiler about a function named "add" that takes two int parameters and returns an int.  No body!
      int x; // tells the compiler about an integer variable named 
      ```

      A declaration is all that is needed to satisfy the compiler. 

      In C++, all definitions also serve as declarations. The converse is not true: all declarations are not definitions. An example of this is the function prototype -- it satisfies the compiler, but not the linker. These declarations that aren’t definitions are called **pure declarations**. Other types of pure declarations include forward declarations for variables and type declarations.
    
21.  **Programs with multiple code files**

    **For Visual Studio users**

    <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200608174954422.png" alt="image-20200608174954422" style="zoom: 50%;" />

22. A **namespace** is a region that allows you to declare names inside of it for the purpose of disambiguation. The namespace provides a scope (called **namespace scope**) to the names declared inside of it -- which simply means that any name declared inside the namespace won’t be mistaken for identical names in other scopes.

    In C++, any name that is not defined inside a class, function, or a namespace is considered to be part of an implicitly defined namespace called the **global namespace** (sometimes also called **the global scope**).
    
    The :: symbol is an operator called the **scope resolution operator**.
    
    Use explicit namespace prefixes to access identifiers defined in a namespace.
    
    ```c++
    #include <iostream> // imports the declaration of std::cout
    using namespace std; // makes std::cout accessible as "cout"
    int cout() // declares our own "cout" function
    {
        return 5;
    }
    int main()
    {
        cout << "Hello, world!"; // Compile error!  Which cout do we want here?  The one in the std namespace or the one we defined above?
        return 0;
    }
    ```
    
    When using a **using directive** in this manner, *any* identifier we define may conflict with *any* identically named identifier in the *std* namespace. Even worse, while an identifier name may not conflict today, it may conflict with new identifiers added to the std namespace in future language revisions. This was the whole point of moving all of the identifiers in the standard library into the *std* namespace in the first place!
    
23. Prior to compilation, the code file goes through a phase known as **translation**.(**translation unit**.)

    **Preprocessor directives** (often just called *directives*) are instructions that start with a *#* symbol and end with a newline (NOT a semicolon). When you *#include* a file, the preprocessor replaces the #include directive with the contents of the included file. The included contents are then preprocessed (along with the rest of the file), and then compiled.	

24. **Macro defines**

    * The *#define* directive can be used to create a macro. In C++, a **macro** is a rule that defines how input text is converted into replacement output text.

    * The *conditional compilation* preprocessor directives allow you to specify under what conditions something will or won’t compile. *#ifdef*, *#ifndef*, and *#endif*.

    * #if 0

      One more common use of conditional compilation involves using *#if 0* to exclude a block of code from being compiled (as if it were inside a comment block)

    **Object-like macros don’t affect other preprocessor directives**

    **The scope of defines**: Directives are resolved before compilation, from top to bottom on a file-by-file basis.

25. **Header files** allow us to put declarations in one location and then import them wherever we need them. This can save a lot of typing in multi-file programs.

    When you #include a file, the content of the included file is inserted at the point of inclusion. This provides a useful way to pull in declarations from another file.

    Header files should generally not contain function and variable definitions, so as not to violate the one definition rule. An exception is made for symbolic constants.

    If a header file is paired with a code file (e.g. add.h with add.cpp), they should both have the same base name (add).

    <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200609155550296.png" alt="image-20200609155550296" style="zoom:50%;" />

    Use angled brackets to include header files that come with the compiler. Use double quotes to include any other header files.

    When including a header file from the standard library, use the no extension version (without the .h) if it exists. User-defined headers should still use a .h extension.

    Order your #includes as follows: your own user-defined headers first, then 3rd party library headers, then standard library headers, with the headers in each section sorted alphabetically.

26. **Header guards** are conditional compilation directives that take the following form:

    ```c++
    #ifndef SOME_UNIQUE_NAME_HERE
    #define SOME_UNIQUE_NAME_HERE
     
    // your declarations (and certain types of definitions) here
     
    #endif
    ```

    square.h:
    
    ```c++
    #ifndef SQUARE_H
    #define SQUARE_H
     
    int getSquareSides(); // forward declaration for getSquareSides
    int getSquarePerimeter(int sideLength); // forward declaration for getSquarePerimeter
     
    #endif
    ```
    
    square.cpp:
    
    ```c++
    #include "square.h"
     
    int getSquareSides() // actual definition for getSquareSides
    {
        return 4;
    }
     
    int getSquarePerimeter(int sideLength)
    {
        return sideLength * getSquareSides();
    }
    ```
    
    main.cpp:
    
    ```c++
    #include "square.h" // square.h is also included once here
    #include <iostream>
     
    int main()
    {
        std::cout << "a square has " << getSquareSides() << "sides\n";
        std::cout << "a square of length 5 has perimeter length " << getSquarePerimeter(5) << '\n';
     
        return 0;
    }
    ```
    
27. That said, if you are going to work on anything of non-trivial complexity, you should have a plan to backup your code. It’s not enough to just zip or copy the directory to another location on your machine (though this is better than nothing). If your system crashes, you’ll lose everything. A good backup strategy involves getting a copy of the code off of your system altogether. There are lots of easy ways to do this: Zip it up and email it to yourself, copy it to Dropbox or another cloud service, FTP it to another machine, copy it to another machine on your local network, or use a version control system residing on another machine or in the cloud (e.g. github). Version control systems have the added advantage of not only being able to restore your files, but also to roll them back to a previous version.

## Debugging programs

1. **Basic debugging tactics**

   * **Debugging tactic #1: Commenting out your code**

     ```c++
     int main()
     {
         getNames(); // ask user to enter a bunch of names
     //    doMaintenance(); // do some random stuff
         sortNames(); // sort them in alphabetical order
         printNames(); // print the sorted list of names
      
         return 0;
     }
     ```

     

   * **Debugging tactic #2: Validating your code flow**

     Another problem common in more complex programs is that the program is calling a function too many or too few times (including not at all).

     In such cases, it can be helpful to place statements at the top of your functions to print the function’s name. That way, when the program runs, you can see which functions are getting called.

     > When printing information for debugging purposes, use std::cerr instead of std::cout. One reason for this is that std::cout may be buffered, which means there may be a pause between when you ask std::cout to output information and when it actually does. If you output using std::cout and then your program crashes immediately afterward, std::cout may or may not have actually output yet. This can mislead you about where the issue is. On the other hand, std::cerr is unbuffered, which means anything you send to it will output immediately. This helps ensure all debug output appears as soon as possible (at the cost of some performance, which we usually don’t care about when debugging).

     When adding temporary debug statements, it can be helpful to **not indent them**. This makes them easier to find for removal later.

   * **Debugging tactic #3: Printing values**

   * **Conditionalizing your debugging code**

   * **Using a logger**

     An alternative approach to conditionalized debugging via the preprocessor is to send your debugging information to a log file. A **log file** is a file (normally stored on disk) that records events that occur in software. The process of writing information to a log file is called **logging**. Most applications and operating systems write log files that can be used to help diagnose issues that occur.

2. All of this tracked information is called your **program state**

   A **debugger** is a computer program that allows the programmer to control how a program executes and examine the program state while the program is running. 

   Don’t neglect learning to use a debugger. As your programs get more complicated, the amount of time you spend learning to use the integrated debugger effectively will pale in comparison to amount of time you save finding and fixing issues.

   **Stepping** is the name for a set of related debugger features that let us execute (step through) our code statement by statement.

   In Visual Studio, the *step into* command can be accessed via *Debug menu > Step Into*, or by pressing the F11 shortcut key.

   Like *step into*, The **step over** command executes the next statement in the normal execution path of the program. However, whereas *step into* will enter function calls and execute them line by line, *step over* will execute an entire function without stopping and return control to you after the function has been executed.

   In Visual Studio, the *step over* command can be accessed via *Debug menu > Step Over*, or by pressing the F10 shortcut key.

3. * This **Run to cursor** command executes the program until execution reaches the statement selected by your cursor. 

     In Visual Studio, the *run to cursor* command can be accessed by right clicking a statement in your code and choosing *Run to Cursor* from the context menu, or by pressing the ctrl-F10 keyboard combo.

   * **Continue**. The **continue** debug command simply continues running the program as per normal, either until the program terminates, or until something triggers control to return back to you again (such as a breakpoint).

     In Visual Studio, the *continue* command can be accessed while already debugging a program via *Debug menu > Continue*, or by pressing the F5 shortcut key.

   * **Start**.  The ***start*** command performs the same action as *continue*, just starting from the beginning of the program. It can only be invoked when not already in a debug session.

     In Visual Studio, the *start* command can be accessed while not debugging a program via *Debug menu > Start Debugging*, or by pressing the F5 shortcut key.

   * **Breakpoints**. A **breakpoint** is a special marker that tells the debugger to stop execution of the program at the breakpoint when running in debug mode.

     In Visual Studio, you can set or remove a breakpoint via *Debug menu > Toggle Breakpoint*, or by right clicking on a statement and choosing *Toggle Breakpoint* from the context menu, or by pressing the F9 shortcut key, or by clicking to the left of the line number (in the light grey area).

   * The **set next statement** command allows us to change the point of execution to some other statement (sometimes informally called *jumping*).
   
4. **Watching variables** In case you are returning, make sure your project is compiled using a debug build configuration.

   In Visual Studio, the watch menu can be found at *Debug menu > Windows > Watch > Watch 1*. Do note that you have to be in debug mode for this option to be enabled, so *step into* your program first.

   Where this window appears (docked left, right, or bottom) may vary. You can change where it is docked by dragging the *Watch 1* tab to a different side of the application window.

   There are typically two different ways to add variables to the watch window:

   1. Pull up the watch window, and type in the name of the variable you would like to watch in the leftmost column of the watch window.
   2. In the code window, right click on the variable you’d like to watch, and choose *Add Watch* (Visual Studio) or *Watch x* (replace x with the variable’s name) (Code::Blocks).

   In Visual Studio, you can see the value of all **local variables** in the *Locals* window, which can be found at at *Debug menu > Windows > Locals*. Note that you have to be in a debug session to activate this window.

5. The **call stack** is a list of all the active functions that have been called to get to the current point of execution. 

   In Visual Studio, the call stack window can be found via *Debug menu > Windows > Call Stack*. Note that you have to be in a debug session to activate this window.

6. One way to address this is to break a single long function into multiple shorter functions. This process of making structural changes to your code without changing its behavior (typically in order to make it more maintainable) is called **refactoring**.

7. **Defensive programming** is a practice whereby the programmer tries to anticipate all of the ways the software could be misused, either by end-users, or by other developers (including the programmer themselves) using the code. These misuses can often be detected and then mitigated (e.g. by asking a user who entered bad input to try again).

## **Fundamental Data Types**

**keywords**: **Escape sequences**, 

1. The terms “integer” and “integral” are similar, but have different meanings. Integers are a specific data type that hold positive and negative whole numbers, including 0. The term “integral types” (which means “like an integer”) includes all of the boolean, characters, and integer types (and thus is a bit broader in definition). Integral types are named so because they are stored in memory as integers, even though they behave slightly differently.

2. Many of the types defined in newer versions of C++ (e.g. std::nullptr_t) use a _t suffix. This suffix means “type”, and it’s a common nomenclature applied to modern types.

3. Signed integer overflow will result in undefined behavior.

4. When doing division with two integers (called **integer division**), C++ always produces an integer result. Since integers can’t hold fractional values, any fractional portion is simply dropped (not rounded!).

5. By definition, unsigned integers cannot overflow. Instead, if a value is out of range, it is divided by one greater than the largest number of the type, and only the remainder kept. (called **wrap around**)

6. Many notable bugs in video game history happened due to wrap around behavior with unsigned integers. In the arcade game Donkey Kong, it’s not possible to go past level 22 due to a bug that leaves the user with not enough bonus time to complete the level. In the PC game Civilization, Gandhi was known for being the first one to use nuclear weapons, which seems contrary to his normally passive nature. Gandhi’s aggression setting was normally set at 1, but if he chose a democratic government, he’d get a -2 modifier. This wrapped around his aggression setting to 255, making him maximally aggressive!

7. Bjarne Stroustrup, the designer of C++, said, “Using an unsigned instead of an int to gain one more bit to represent positive integers is almost never a good idea”.

8. To help with cross-platform portability, C99 defined a set of **fixed-width integers** (in the stdint.h header) that are guaranteed to have the same size on any architecture.

   > e.g. std::int16_t

   The fast type (**std::int_fast#_t**) provides the fastest signed integer type with a width of at least # bits (where # = 8, 16, 32, or 64). For example, *std::int_fast32_t* will give you the fastest signed integer type that’s at least 32 bits.

9. For simplicity, it’s best to avoid *std::int8_t* and *std::uint8_t* (and the related fast and least types) altogether (use *std::int16_t* or *std::uint16_t* instead). However, if you do use *std::int8_t* or *std::uint8_t*, you should be careful of anything that would interpret *std::int8_t* or *std::uint8_t* as a char instead of an integer (this includes *std::cout* and *std::cin*).

10. Avoid the following if possible:

    - Unsigned types, unless you have a compelling reason.
    - The 8-bit fixed-width integer types.
    - Any compiler-specific fixed-width integers -- for example, Visual Studio defines __int8, __int16, etc…

11. By definition, any object larger than the largest value *size_t* can hold is considered ill-formed (and will cause a compile error), as the *sizeof* operator would not be able to return the size without wrapping around.

12. Here’s the most important thing to understand: The digits in the significand (the part before the ‘e’) are called the **significant digits**. The number of significant digits defines a number’s **precision**. The more digits in the significand, the more precise a number is.

13. | Category       | Type        | Minimum Size | Typical Size       |
    | :------------- | :---------- | :----------- | :----------------- |
    | floating point | float       | 4 bytes      | 4 bytes            |
    |                | double      | 8 bytes      | 8 bytes            |
    |                | long double | 8 bytes      | 8, 12, or 16 bytes |

    When using floating point literals, always include at least one decimal place (even if the decimal is 0). This helps the compiler understand that the number is a floating point number and not an integer.

    ```c++
    int x{5}; // 5 means integer
    double y{5.0}; // 5.0 is a floating point literal (no suffix means double type by default)
    float z{5.0f}; // 5.0 is a floating point literal, f suffix means float type
    ```

14. When precision is lost because a number can’t be stored precisely, this is called a **rounding error**.

    Favor double over float unless space is at a premium, as the lack of precision in a float will often lead to inaccuracies.

15. If you want std::cout to print “true” or “false” instead of 0 or 1, you can use *std::boolalpha*. Here’s an example:

    ```c++
     std::cout << std::boolalpha; // print bools as true or false
     
        std::cout << true << '\n';
        std::cout << false << '\n';
    ```

    You can’t initialize a Boolean with an integer using uniform initialization:

    ```c++
    #include <iostream>
     
    int main()
    {
    	bool b{ 4 }; // error: narrowing conversions disallowed
    	std::cout << b;
    	
    	return 0;
    }
    ```

    However, in any context where an integer can be converted to a Boolean , the integer *0* is converted to *false*, and any other integer is converted to *true*.

    ```c++
    #include <iostream>
     
    int main()
    {
    	std::cout << std::boolalpha; // print bools as true or false
     
    	bool b1 = 4 ; // copy initialization allows implicit conversion from int to bool
    	std::cout << b1 << '\n';
     
    	bool b2 = 0 ; // copy initialization allows implicit conversion from int to bool
    	std::cout << b2 << '\n';
     
    	
    	return 0;
    }
    ```

16. **Inputting Boolean values**

    ```c++
    #include <iostream>
     
    int main()
    {
    	bool b{}; // default initialize to false
    	std::cout << "Enter a boolean value: ";
    	std::cin >> b;
    	std::cout << "You entered: " << b << '\n';
     
    	return 0;
    }
    ```

    > ```c++
    > Enter a Boolean value: true
    > You entered: 0
    > ```

    It turns out that *std::cin* only accepts two inputs for Boolean variables: 0 and 1 (*not* true or false). Any other inputs will cause *std::cin* to silently fail. In this case, because we entered *true*, *std::cin* silently failed. In C++11 or newer, a failed input will also zero-out the variable, so *b* also gets assigned value 0. Consequently, when *std::cout* prints a value for *b*, it prints 0.
    
17. | Code | Symbol                          | Code | Symbol  | Code | Symbol | Code | Symbol       |
    | :--- | :------------------------------ | :--- | :------ | :--- | :----- | :--- | :----------- |
    | 0    | NUL (null)                      | 32   | (space) | 64   | @      | 96   | `            |
    | 1    | SOH (start of header)           | 33   | !       | 65   | A      | 97   | a            |
    | 2    | STX (start of text)             | 34   | ”       | 66   | B      | 98   | b            |
    | 3    | ETX (end of text)               | 35   | #       | 67   | C      | 99   | c            |
    | 4    | EOT (end of transmission)       | 36   | $       | 68   | D      | 100  | d            |
    | 5    | ENQ (enquiry)                   | 37   | %       | 69   | E      | 101  | e            |
    | 6    | ACK (acknowledge)               | 38   | &       | 70   | F      | 102  | f            |
    | 7    | BEL (bell)                      | 39   | ’       | 71   | G      | 103  | g            |
    | 8    | BS (backspace)                  | 40   | (       | 72   | H      | 104  | h            |
    | 9    | HT (horizontal tab)             | 41   | )       | 73   | I      | 105  | i            |
    | 10   | LF (line feed/new line)         | 42   | *       | 74   | J      | 106  | j            |
    | 11   | VT (vertical tab)               | 43   | +       | 75   | K      | 107  | k            |
    | 12   | FF (form feed / new page)       | 44   | ,       | 76   | L      | 108  | l            |
    | 13   | CR (carriage return)            | 45   | -       | 77   | M      | 109  | m            |
    | 14   | SO (shift out)                  | 46   | .       | 78   | N      | 110  | n            |
    | 15   | SI (shift in)                   | 47   | /       | 79   | O      | 111  | o            |
    | 16   | DLE (data link escape)          | 48   | 0       | 80   | P      | 112  | p            |
    | 17   | DC1 (data control 1)            | 49   | 1       | 81   | Q      | 113  | q            |
    | 18   | DC2 (data control 2)            | 50   | 2       | 82   | R      | 114  | r            |
    | 19   | DC3 (data control 3)            | 51   | 3       | 83   | S      | 115  | s            |
    | 20   | DC4 (data control 4)            | 52   | 4       | 84   | T      | 116  | t            |
    | 21   | NAK (negative acknowledge)      | 53   | 5       | 85   | U      | 117  | u            |
    | 22   | SYN (synchronous idle)          | 54   | 6       | 86   | V      | 118  | v            |
    | 23   | ETB (end of transmission block) | 55   | 7       | 87   | W      | 119  | w            |
    | 24   | CAN (cancel)                    | 56   | 8       | 88   | X      | 120  | x            |
    | 25   | EM (end of medium)              | 57   | 9       | 89   | Y      | 121  | y            |
    | 26   | SUB (substitute)                | 58   | :       | 90   | Z      | 122  | z            |
    | 27   | ESC (escape)                    | 59   | ;       | 91   | [      | 123  | {            |
    | 28   | FS (file separator)             | 60   | <       | 92   | \      | 124  | \|           |
    | 29   | GS (group separator)            | 61   | =       | 93   | ]      | 125  | }            |
    | 30   | RS (record separator)           | 62   | >       | 94   | ^      | 126  | ~            |
    | 31   | US (unit separator)             | 63   | ?       | 95   | _      | 127  | DEL (delete) |

    Codes 0-31 are called the unprintable chars, and they’re mostly used to do formatting and control printers. Most of these are obsolete now.

    Codes 32-127 are called the printable characters, and they represent the letters, number characters, and punctuation that most computers use to display basic English text.

18. A **type cast** creates a value of one type from a value of another type. To convert between fundamental data types (for example, from a char to an int, or vice versa), we use a type cast called a **static cast**.

    ```c++
    static_cast<new_type>(expression)
    ```

    > **Key insight**
    >
    > Whenever you see C++ syntax (excluding the preprocessor) that makes use of **angled brackets**, the thing between the angled brackets will most likely be a type. This is typically how C++ deals with concepts that need a parameterizable type.

19. Note that std::cin will let you enter multiple characters. However, variable *ch* can only hold 1 character. Consequently, only the first input character is extracted into variable *ch*. The rest of the user input is left in the input buffer that std::cin uses, and can be extracted with subsequent calls to std::cin.

20. **Escape sequences**

    | Name            | Symbol     | Meaning                                                      |
    | :-------------- | :--------- | :----------------------------------------------------------- |
    | Alert           | \a         | Makes an alert, such as a beep                               |
    | Backspace       | \b         | Moves the cursor back one space                              |
    | Formfeed        | \f         | Moves the cursor to next logical page                        |
    | Newline         | \n         | Moves cursor to next line                                    |
    | Carriage return | \r         | Moves cursor to beginning of line                            |
    | Horizontal tab  | \t         | Prints a horizontal tab                                      |
    | Vertical tab    | \v         | Prints a vertical tab                                        |
    | Single quote    | \’         | Prints a single quote                                        |
    | Double quote    | \”         | Prints a double quote                                        |
    | Backslash       | \\         | Prints a backslash.                                          |
    | Question mark   | \?         | Prints a question mark. No longer relevant. You can use question marks unescaped. |
    | Octal number    | \(number)  | Translates into char represented by octal                    |
    | Hex number      | \x(number) | Translates into char represented by hex number               |

21. Much like ASCII maps the integers 0-127 to American English characters, other character encoding standards exist to map integers (of varying sizes) to characters in other languages. The most well-known mapping outside of ASCII is the Unicode standard, which maps over 110,000 integers to characters in many different languages. Because Unicode contains so many code points, a single Unicode code point needs 32-bits to represent a character (called UTF-32). However, Unicode characters can also be encoded using multiple 16-bit or 8-bit characters (called UTF-16 and UTF-8 respectively).

22. **Literals**

    In programming, a **constant** is a fixed value that may not be changed. C++ has two kinds of constants: literal constants, and symbolic constants.

    **Literal constants** (usually just called **literals**) are values inserted directly into the code. For example:

    ```c++
    return 5; // 5 is an integer literal
    bool myNameIsAlex { true }; // true is a boolean literal
    std::cout << 3.4; // 3.4 is a double literal
    ```

    Just like objects have a type, all literals have a type. The type of a literal is assumed from the value and format of the literal itself.

    | Literal value        | Examples        | Default type        |
    | :------------------- | :-------------- | :------------------ |
    | integral value       | 5, 0, -3        | int                 |
    | boolean value        | true, false     | bool                |
    | floating point value | 3.4, -2.2       | double (not float)! |
    | char value           | ‘a’             | char                |
    | C-style string       | “Hello, world!” | const char[14]      |

    If the default type of a literal is not as desired, you can change the type of a literal by adding a suffix:

    | Data Type | Suffix                                    | Meaning            |
    | :-------- | :---------------------------------------- | :----------------- |
    | int       | u or U                                    | unsigned int       |
    | int       | l or L                                    | long               |
    | int       | ul, uL, Ul, UL, lu, lU, Lu, or LU         | unsigned long      |
    | int       | ll or LL                                  | long long          |
    | int       | ull, uLL, Ull, ULL, llu, llU, LLu, or LLU | unsigned long long |
    | double    | f or F                                    | float              |
    | double    | l or L                                    | long double        |

    New programmers are often confused about why the following doesn’t work as expected:

    ```c++
    float f { 4.1 }; // warning: 4.1 is a double suffix, not a float suffix
    ```

    **String literals**

    ```c++
    std::cout << "Hello, world!"; // "Hello, world!" is a C-style string literal
    std::cout << "Hello," " world!"; // C++ will concatenate sequential string literals
    ```

    **Scientific notation for floating point literals**

    ```c++
    double pi { 3.14159 }; // 3.14159 is a double literal in standard notation
    double avogadro { 6.02e23 }; // 6.02 x 10^23 is a double literal in scientific notation
    ```

    To use an octal literal, prefix your literal with a 0.

    To use a hexadecimal literal, prefix your literal with 0x.

    In C++14, we can assign binary literals by using the 0b prefix.

    By default, C++ prints values in decimal. However, you can tell it to print in other formats. Printing in decimal, octal, or hex is easy via use of std::dec, std::oct, and std::hex:

    ```c++
    #include <iostream>
     
    int main()
    {
        int x { 12 };
        std::cout << x << '\n'; // decimal (by default)
        std::cout << std::hex << x << '\n'; // hexadecimal
        std::cout << x << '\n'; // now hexadecimal
        std::cout << std::oct << x << '\n'; // octal
        std::cout << std::dec << x << '\n'; // return to decimal
        std::cout << x << '\n'; // decimal
     
        return 0;
    }
    ```

    A **magic number** is a literal (usually a number) in the middle of the code that does not have any context. 

    Consider the following snippet:

    ```c++
    int maxStudents{ numClassrooms * 30 };
    ```

23. **const, constexpr, and symbolic constant**

    To make a variable constant, simply put the const keyword either before or after the variable type, like so:

    ```c++
    const double gravity { 9.8 }; // preferred use of const before type
    int const sidesInSquare { 4 }; // okay, but not preferred
    ```

    Declaring a variable as const prevents us from inadvertently changing its value:
    
    Note that const variables can be initialized from other variables (including non-const ones):
    
    Const is often used with function parameters:
    
    **Runtime constants** are those whose initialization values can only be resolved at runtime (when your program is running).  *usersAge* relies on user input (which can only be given at runtime) and *myValue* depends on the value passed into the function (which is only known at runtime).
    
    **Compile-time constants** are those whose initialization values can be resolved at compile-time (when your program is compiling). 
    
    To help provide more specificity, C++11 introduced the keyword **constexpr**, which ensures that a constant must be a compile-time constant:
    
    ```c++
    constexpr double gravity { 9.8 }; // ok, the value of 9.8 can be resolved at compile-time
    constexpr int sum { 4 + 5 }; // ok, the value of 4 + 5 can be resolved at compile-time
     
    std::cout << "Enter your age: ";
    int age;
    std::cin >> age;
    constexpr int myAge { age }; // not okay, age can not be resolved at compile-time
    ```
    
    Const variables act exactly like normal variables in every case except that they can not be assigned to, so there’s no particular reason they need to be denoted as special.
    
24. **Symbolic constants**

    * **Bad: Using object-like macros with a substitution parameter as symbolic constants**

      ```c++
      #define identifier substitution_text
      ```

      **Avoid using #define to create symbolic constants macros.**

    * **A better solution: Use constexpr variables**

      ```c++
      constexpr int maxStudentsPerClass { 30 };
      constexpr int maxNameLength { 30 };
      ```

      Because these are just normal variables, they are watchable in the debugger, have normal scoping, and avoid other weird behaviors.

      > **Use constexpr variables to provide a name and context for your magic numbers.**

25. **Using symbolic constants throughout a multi-file program**

    There are multiple ways to facilitate this within C++, but the following is probably easiest:

    1) Create a header file to hold these constants
    2) Inside this header file, declare a namespace 
    3) Add all your constants inside the namespace (make sure they’re *constexpr* in C++11/14, or *inline constexpr* in C++17 or newer)
    4) #include the header file wherever you need it

    constants.h (C++11/14):

    ```c++
    #ifndef CONSTANTS_H
    #define CONSTANTS_H
     
    // define your own namespace to hold constants
    namespace constants
    {
        constexpr double pi { 3.14159 };
        constexpr double avogadro { 6.0221413e23 };
        constexpr double my_gravity { 9.2 }; // m/s^2 -- gravity is light on this planet
        // ... other related constants
    }
    #endif
    ```

    In C++17, prefer “inline constexpr” instead:

    constants.h (C++17 or newer):

    ```c++
    #ifndef CONSTANTS_H
    #define CONSTANTS_H
    // define your own namespace to hold constants
    namespace constants
    {
        inline constexpr double pi { 3.14159 }; // inline constexpr is C++17 or newer only
        inline constexpr double avogadro { 6.0221413e23 };
        inline constexpr double my_gravity { 9.2 }; // m/s^2 -- gravity is light on this planet
        // ... other related constants
    }
    #endif
    ```

    Use the scope resolution operator (::) to access your constants in .cpp files:

    main.cpp:

    ```c++
    #include "constants.h"
    #include <iostream>
     
    int main()
    {
        std::cout << "Enter a radius: ";
        int radius{};
        std::cin >> radius;
     
        double circumference { 2.0 * radius * constants::pi };
        std::cout << "The circumference is: " << circumference << '\n';
     
        return 0;
    }
    ```

## Operators

1. Notes:

   - Precedence level 1 is the highest precedence level, and level 17 is the lowest. Operators with a higher precedence level get evaluated first.
   - L->R means left to right associativity.
   - R->L means right to left associativity.

   | Prec/Ass | Operator                                                     | Description                                                  | Pattern                                                      |
   | :------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
   | 1 None   | :: ::                                                        | Global scope (unary) Namespace scope (binary)                | ::name class_name::member_name                               |
   | 2 L->R   | () () () {} type() type{} [] . -> ++ –– typeid const_cast dynamic_cast reinterpret_cast static_cast | Parentheses Function call Initialization Uniform initialization (C++11) Functional cast Functional cast (C++11) Array subscript Member access from object Member access from object ptr Post-increment Post-decrement Run-time type information Cast away const Run-time type-checked cast Cast one type to another Compile-time type-checked cast | (expression) function_name(parameters) type name(expression) type name{expression} new_type(expression) new_type{expression} pointer[expression] object.member_name object_pointer->member_name lvalue++ lvalue–– typeid(type) or typeid(expression) const_cast<type>(expression) dynamic_cast<type>(expression) reinterpret_cast<type>(expression) static_cast<type>(expression) |
   | 3 R->L   | + - ++ –– ! ~ (type) sizeof & * new new[] delete delete[]    | Unary plus Unary minus Pre-increment Pre-decrement Logical NOT Bitwise NOT C-style cast Size in bytes Address of Dereference Dynamic memory allocation Dynamic array allocation Dynamic memory deletion Dynamic array deletion | +expression -expression ++lvalue ––lvalue !expression ~expression (new_type)expression sizeof(type) or sizeof(expression) &lvalue *expression new type new type[expression] delete pointer delete[] pointer |
   | 4 L->R   | ->* .*                                                       | Member pointer selector Member object selector               | object_pointer->*pointer_to_member object.*pointer_to_member |
   | 5 L->R   | * / %                                                        | Multiplication Division Modulus                              | expression * expression expression / expression expression % expression |
   | 6 L->R   | + -                                                          | Addition Subtraction                                         | expression + expression expression - expression              |
   | 7 L->R   | << >>                                                        | Bitwise shift left Bitwise shift right                       | expression << expression expression >> expression            |
   | 8 L->R   | < <= > >=                                                    | Comparison less than Comparison less than or equals Comparison greater than Comparison greater than or equals | expression < expression expression <= expression expression > expression expression >= expression |
   | 9 L->R   | == !=                                                        | Equality Inequality                                          | expression == expression expression != expression            |
   | 10 L->R  | &                                                            | Bitwise AND                                                  | expression & expression                                      |
   | 11 L->R  | ^                                                            | Bitwise XOR                                                  | expression ^ expression                                      |
   | 12 L->R  | \|                                                           | Bitwise OR                                                   | expression \| expression                                     |
   | 13 L->R  | &&                                                           | Logical AND                                                  | expression && expression                                     |
   | 14 L->R  | \|\|                                                         | Logical OR                                                   | expression \|\| expression                                   |
   | 15 R->L  | ?: = *= /= %= += -= <<= >>= &= \|= ^=                        | Conditional Assignment Multiplication assignment Division assignment Modulus assignment Addition assignment Subtraction assignment Bitwise shift left assignment Bitwise shift right assignment Bitwise AND assignment Bitwise OR assignment Bitwise XOR assignment | expression ? expression : expression lvalue = expression lvalue *= expression lvalue /= expression lvalue %= expression lvalue += expression lvalue -= expression lvalue <<= expression lvalue >>= expression lvalue &= expression lvalue \|= expression lvalue ^= expression |
   | 16 R->L  | throw                                                        | Throw expression                                             | throw expression                                             |
   | 17 L->R  | ,                                                            | Comma operator                                               | expression, expression                                       |

2. Prior to C++11, integer division with a negative operand could round up or down. Thus `-5 / 3` could result in -1 or -2. This was fixed in C++11, which always drops the fraction (rounds towards 0).

3. **Using static_cast<> to do floating point division with integers**

   ```c++
    std::cout << "double / int = " << static_cast<double>(x) / y << '\n';
   ```

4. The **modulus operator** (also informally known as the *remainder operator*) is an operator that returns the remainder after doing an integer division. 

5. Note that the parameters (and return value) of function pow() are of type double. Due to **rounding errors** in floating point numbers, the results of pow() may not be precise (even if you pass it integers or whole numbers).

   If you want to do integer exponentiation, you’re best off using your own function to do so. The following function implements integer exponentiation (using the non-intuitive “exponentiation by squaring” algorithm for efficiency):

   ```c++
   #include <cstdint> // for std::int_fast64_t
    
   // note: exp must be non-negative
   std::int_fast64_t pow(int base, int exp)
   {
       std::int_fast64_t result{ 1 };
       while (exp)
       {
           if (exp & 1)
               result *= base;
           exp >>= 1;
           base *= base;
       }
       return result;
   }
   ```

6. A function or expression is said to have a **side effect** if it does anything that persists beyond the life of the function or expression itself. Common examples of side effects include changing the value of objects, doing input or output, or updating a graphical user interface (e.g. enabling or disabling a button).

   C++ does not define the order of evaluation for function arguments or operator operands.

   Don’t use a variable that has a side effect applied to it more than once in a given statement. If you do, the result may be undefined.
   
7. **The comma operator**

   | Operator | Symbol | Form | Operation                             |
   | :------- | :----- | :--- | :------------------------------------ |
   | Comma    | ,      | x, y | Evaluate x then y, returns value of y |

   Avoid using the comma operator, except within *for loops*.

   **The conditional operator**

   | Operator    | Symbol | Form      | Operation                                                    |
   | :---------- | :----- | :-------- | :----------------------------------------------------------- |
   | Conditional | ?:     | c ? x : y | If c is nonzero (true) then evaluate x, otherwise evaluate y |
   
   Always parenthesize the conditional part of the conditional operator, and consider parenthesizing the whole thing as well.
   
8. The most common method of doing floating point equality involves using a function that looks to see if two numbers are *almost* the same. If they are “close enough”, then we call them equal. The value used to represent “close enough” is traditionally called **epsilon**. 

9. Bit manipulation is one of the few times when you should unambiguously use unsigned integers (or std::bitset).

10. std::bitset provides 4 key functions that are useful for doing bit manipulation:

    - test() allows us to query whether a bit is a 0 or 1
    - set() allows us to turn a bit on (this will do nothing if the bit is already on)
    - reset() allows us to turn a bit off (this will do nothing if the bit is already off)
    - flip() allows us to flip a bit value from a 0 to a 1 or vice versa

    ```c++
    #include <bitset>
    #include <iostream>
     
    int main()
    {
        std::bitset<8> bits{ 0b0000'0101 }; // we need 8 bits, start with bit pattern 0000 0101
        bits.set(3); // set bit position 3 to 1 (now we have 0000 1101)
        bits.flip(4); // flip bit 4 (now we have 0001 1101)
        bits.reset(4); // set bit 4 back to 0 (now we have 0000 1101)
     
        std::cout << "All the bits: " << bits << '\n';
        std::cout << "Bit 3 has value: " << bits.test(3) << '\n';
        std::cout << "Bit 4 has value: " << bits.test(4) << '\n';
     
        return 0;
    }
    ```

11. **The bitwise operators**

    | Operator    | Symbol | Form   | Operation                          |
    | :---------- | :----- | :----- | :--------------------------------- |
    | left shift  | <<     | x << y | all bits in x shifted left y bits  |
    | right shift | >>     | x >> y | all bits in x shifted right y bits |
    | bitwise NOT | ~      | ~x     | all bits in x flipped              |
    | bitwise AND | &      | x & y  | each bit in x AND each bit in y    |
    | bitwise OR  | \|     | x \| y | each bit in x OR each bit in y     |
    | bitwise XOR | ^      | x ^ y  | each bit in x XOR each bit in y    |

12. **two’s complement** 补码

## Object Scope and Conversions

1. When blocks are nested, the enclosing block is typically called the **outer block** and the enclosed block is called the **inner block** or **nested block**.

2. C++ allows us to define our own namespaces via the `namespace` keyword. Namespaces that you create for your own declarations are called **user-defined namespaces**. Namespaces provided by C++ (such as the `global namespace`) or by libraries (such as `namespace std`) are not considered user-defined namespaces.

3. **Accessing a namespace with the scope resolution operator (::)**

   The scope resolution operator can also be used without any preceding namespace (eg. `::doSomething`). In such a case, the identifier (e.g. `doSomething`) is looked for in the global namespace

4. **Multiple namespace blocks allowed**

   The standard library makes extensive use of this feature, as each standard library header file contains its declarations inside a `namespace std` block contained within that header file. Otherwise the entire standard library would have to be defined in a single header file!

   Note that this capability also means you could add your own functionality to the `std` namespace. Doing so causes undefined behavior most of the time, because the `std` namespace has a special rule, prohibiting extension from user code.

5. **Nested namespaces**

   ```c++
   #include <iostream> 
   namespace foo
   {
       namespace goo // goo is a namespace inside the foo namespace
       {
           int add(int x, int y)
           {
               return x + y;
           }
       }
   }
    
   int main()
   {
       std::cout << foo::goo::add(1, 2) << '\n';
       return 0;
   }
   ```

   Note that because namespace `goo` is inside of namespace `foo`, we access `add` as `foo::goo::add`.

   In C++17, nested namespaces can also be declared this way:

   ```c++
   #include <iostream> 
   namespace foo::goo // goo is a namespace inside the foo namespace (C++17 style)
   {
           int add(int x, int y)
           {
               return x + y;
           }
   }
    
   int main()
   {
       std::cout << foo::goo::add(1, 2) << '\n';
       return 0;
   }
   ```

   Because typing the fully qualified name of a variable or function inside a nested namespace can be painful, C++ allows you to create **namespace aliases**, which allow us to temporarily shorten a long sequence of namespaces into something shorter:

   ```c++
   #include <iostream>
   namespace foo
   {
   	namespace goo
   	{
   	        int add(int x, int y)
           	{
   	            return x + y;
           	}
   	}
   }
    
   int main()
   {
   	namespace boo = foo::goo; // boo now refers to foo::goo
    
   	std::cout << boo::add(1, 2) << '\n'; // This is really foo::goo::add()
    
   	return 0;
   } // The boo alias ends here
   ```

6. Local variables have **block scope**, which means they are *in scope* from their point of definition to the end of the block they are defined within.

   Although function parameters are not defined inside the function body, for typical functions they can be considered to be part of the scope of the function body block.

   **All variable names within a scope must be unique**

   **Local variables have automatic storage duration**

   > A variable’s **storage duration** (usually just called **duration**) determines what rules govern when and how a variable will be created and destroyed. In most cases, a variable’s storage duration directly determines its `lifetime`.
   >
   > For example, local variables have **automatic storage duration**, which means they are created at the point of definition and destroyed at the end of the block they are defined in.

   **Local variables in nested blocks**

   * Identifiers have another property named `linkage`. An identifier’s **linkage** determines whether other declarations of that name refer to the same object or not.

     Local variables have `no linkage`, which means that each declaration refers to a unique object. For example:

     ```c++
     int main()
     {
         int x { 2 }; // local variable, no linkage
      
         {
             int x { 3 }; // this identifier x refers to a different object than the previous x
         }
      
         return 0;
     }
     ```

     Scope and linkage may seem somewhat similar. However, scope defines where a single declaration can be seen and used. Linkage defines whether multiple declarations refer to the same object or not.

   **Variables should be defined in the most limited scope**
   
7. Each block defines its own scope region. So what happens when we have a variable inside a nested block that has the same name as a variable in an outer block? When this happens, the nested variable “hides” the outer variable in areas where they are both in scope. This is called **name hiding** or **shadowing**.

   Similar to how variables in a nested block can shadow variables in an outer block, local variables with the same name as a global variable will shadow the global variable wherever the local variable is in scope:

   ```c++
   #include <iostream>
   int value { 5 }; // global variable
    
   void foo()
   {
       std::cout << "global variable value: " << value << '\n'; // value is not shadowed here, so this refers to the global value
   }
    
   int main()
   {
       int value { 7 }; // hides the global variable value until the end of this block
    
       ++value; // increments local value, not global value
    
       std::cout << "local variable value: " << value << '\n';
    
       foo();
    
       return 0;
   } // local value is destroyed
   ```

   Shadowing of local variables should generally be avoided, as it can lead to inadvertent errors where the wrong variable is used or modified. Some compilers will issue a warning when a variable is shadowed.

8. Global variables with internal linkage are sometimes called **internal variables**.

   To make a non-constant global variable internal, we use the `static` keyword.

   ```c++
   static int g_x; // non-constant globals have external linkage by default, but can be given internal linkage via the static keyword
   ```

   The use of the `static` keyword above is an example of a **storage class specifier**, which sets both the name’s linkage and its storage duration (but not its scope). The most commonly used `storage class specifier` values are `static`, `extern`, and `mutable`. The term `storage class specifier` is mostly used in technical documentations.

   > Key Differences between Identifier and Variable
   >
   > 1. Both an identifier and a variable are the names allotted by users to a particular entity in a program. The identifier is only used to identify an entity uniquely in a program at the time of execution whereas, a variable is a name given to a memory location, that is used to hold a value.
   > 2. Variable is only a kind of identifier, other kinds of identifiers are function names, class names, structure names, etc. So it can be said that all variables are identifiers whereas, vice versa is not true.
   >
   > As identifier and variable names are user-defined names, it should be taken care that no two identifiers or no two variable names in a program should be the same. It will create a problem of ambiguity in a program.

9. **Functions with internal linkage**

   Because linkage is a **property of an identifier** (not of a variable), function identifiers have the same linkage property that variable identifiers do. Functions default to external linkage (which we’ll cover in the next lesson), but can be set to internal linkage via the `static` keyword.

10. An identifier with **external linkage** can be seen and used both from the file in which it is defined, and from other code files (via a forward declaration).

    * **Functions have external linkage by default**

      In order to call a function defined in another file, you must place a `forward declaration` for the function in any other files wishing to use the function. The forward declaration tells the compiler about the existence of the function, and the linker connects the function calls to the actual function definition.

      Here’s an example:

      a.cpp:

      ```c++
      #include <iostream>
       
      void sayHi() // this function has external linkage, and can be seen by other files
      {
          std::cout << "Hi!";
      }
      ```

      main.cpp:

      ```c++
      void sayHi(); // forward declaration for function sayHi, makes sayHi accessible in this file
       
      int main()
      {
          sayHi(); // call to function defined in another file, linker will connect this call to the function definition
       
          return 0;
      }
      ```

    * **Global variables with external linkage**

      Global variables with external linkage are sometimes called **external variables**. To make a global variable external (and thus accessible by other files), we can use the `extern` keyword to do so.

      Non-const global variables are external by default (if used, the `extern` keyword will be ignored).

      To actually use an external global variable that has been defined in another file, you also must place a `forward declaration` for the global variable in any other files wishing to use the variable. For variables, creating a forward declaration is also done via the `extern` keyword (with no initialization value).

      Here is an example of using a variable forward declaration:

      a.cpp: (definitions)

      ```c++
      // global variable definitions
      int g_x { 2 }; // non-constant globals have external linkage by default
      extern const int g_y { 3 }; // this extern gives g_y external linkage
      ```

      main.cpp: (declarations)

      ```c++
      #include <iostream>
       
      extern int g_x; // this extern is a forward declaration of a variable named g_x that is defined somewhere else
      extern const int g_y; // this extern is a forward declaration of a const variable named g_y that is defined somewhere else
       
      int main()
      {
          std::cout << g_x; // prints 2
       
          return 0;
      }
      ```

      Note that the `extern` keyword has different meanings in different contexts. In some contexts, `extern` means “give this variable external linkage”. In other contexts, `extern` means “this is a forward declaration for an external variable that is defined somewhere else”. Yes, this is confusing, so we summarize all of these usages in lesson [6.11 -- Scope, duration, and linkage summary](https://www.learncpp.com/cpp-tutorial/scope-duration-and-linkage-summary/).

      **warnings**

      * If you want to define an uninitialized non-const global variable, do not use the extern keyword, otherwise C++ will think you’re trying to make a forward declaration for the variable.
      * Although constexpr variables can be given external linkage via the `extern` keyword, they can not be forward declared, so there is no value in giving them external linkage.

      However, informally, the term “file scope” is more often applied to global variables with internal linkage, and “global scope” to global variables with external linkage (since they can be used across the whole program, with the appropriate forward declarations).
    
11. **Global constants as internal variables**

    There are multiple ways to facilitate this within C++. Pre-C++17, the following is probably the easiest and most common:

    1) Create a header file to hold these constants
    2) Inside this header file, define a namespace (discussed in lesson [6.2 -- User-defined namespaces](https://www.learncpp.com/cpp-tutorial/user-defined-namespaces/))
    3) Add all your constants inside the namespace (make sure they’re *constexpr*)
    4) #include the header file wherever you need it

    For example:

    constants.h:

    ```c++
    #ifndef CONSTANTS_H
    #define CONSTANTS_H
     
    // define your own namespace to hold constants
    namespace constants
    {
        // constants have internal linkage by default
        constexpr double pi { 3.14159 };
        constexpr double avogadro { 6.0221413e23 };
        constexpr double my_gravity { 9.2 }; // m/s^2 -- gravity is light on this planet
        // ... other related constants
    }
    #endif
    ```

    Then use the scope resolution operator (::) with the namespace name to the left, and your variable name to the right in order to access your constants in .cpp files:

    main.cpp:

    ```c++
    #include "constants.h" // include a copy of each constant in this file
     
    int main()
    {
        std::cout << "Enter a radius: ";
        int radius{};
        std::cin >> radius;
     
        std::cout << "The circumference is: " << 2 * radius * constants::pi;
    }
    ```

    Because const globals have internal linkage, each .cpp file gets an independent version of the global variable that the linker can’t see. In most cases, because these are const, the compiler will simply optimize the variables away.

    > The term “optimizing away” refers to any process where the compiler optimizes the performance of your program by removing things in a way that doesn’t affect the output of your program.

    **Global constants as external variables**

    The above method has a few potential downsides.

    While this is simple (and fine for smaller programs), every time constants.h gets #included into a different code file, each of these variables is copied into the including code file. Therefore, if constants.h gets included into 20 different code files, each of these variables is duplicated 20 times. Header guards won’t stop this from happening, as they only prevent a header from being included more than once into a single including file, not from being included one time into multiple different code files. This introduces two challenges:
    1) Changing a single constant value would require recompiling every file that includes the constants header, which can lead to lengthy rebuild times for larger projects.
    2) If the constants are large in size and can’t be optimized away, this can use a lot of memory.

    One way to avoid these problems is by turning these constants into external variables, since we can then have a single variable (initialized once) that is shared across all files. In this method, we’ll define the constants in a .cpp file (to ensure the definitions only exist in one place), and put forward declarations in the header (which will be included by other files).

    > We use const instead of constexpr in this method because constexpr variables can’t be forward declared, even if they have external linkage.

    constants.cpp:

    ```c++
    #include "constants.h"
     
    namespace constants
    {
        // actual global variables
        extern const double pi { 3.14159 };
        extern const double avogadro { 6.0221413e23 };
        extern const double my_gravity { 9.2 }; // m/s^2 -- gravity is light on this planet
    }
    ```

    constants.h:

    ```c++
    #ifndef CONSTANTS_H
    #define CONSTANTS_H
     
    namespace constants
    {
        // since the actual variables are inside a namespace, the forward declarations need to be inside a namespace as well
        extern const double pi;
        extern const double avogadro;
        extern const double my_gravity;
    }
     
    #endif
    ```

    Use in the code file stays the same:

    main.cpp:

    ```c++
    #include "constants.h" // include all the forward declarations
     
    int main()
    {
        std::cout << "Enter a radius: ";
        int radius{};
        std::cin >> radius;
     
        std::cout << "The circumference is: " << 2 * radius * constants::pi;
    }
    ```

    We can include `constants.h` into as many code files as we want, but these variables will only be instantiated once and shared across all code files.

    > Best practice
    >
    > If you need global constants and your compiler is C++17 capable, prefer defining inline constexpr global variables in a header file.

12. **Global variables are one of the most historically abused concepts in the language.** When developers tell you that global variables are evil, they’re usually not talking about *all* global variables. They’re mostly talking about non-const global variables.

    **Why (non-const) global variables are evil**: By far the biggest reason non-const global variables are dangerous is because their values can be changed by *any* function that is called, and there is no easy way for the programmer to know that this will happen. 

    ```c++
    int g_mode; // declare global variable (will be zero-initialized by default)
     
    void doSomething()
    {
        g_mode = 2; // set the global g_mode variable to 2
    }
     
    int main()
    {
        g_mode = 1; // note: this sets the global g_mode variable to 1.  It does not declare a local g_mode variable!
     
        doSomething();
     
        // Programmer still expects g_mode to be 1
        // But doSomething changed it to 2!
     
        if (g_mode == 1)
            std::cout << "No threat detected.\n";
        else
            std::cout << "Launching nuclear missiles...\n";
     
        return 0;
    }
    ```

    In short, global variables make the program’s state unpredictable. Every function call becomes potentially dangerous, and the programmer has no easy way of knowing which ones are dangerous and which ones aren’t! Local variables are much safer because other functions can not affect them directly.

    Global variables also make your program less modular and less flexible. A function that utilizes nothing but its parameters and has no side effects is perfectly modular. Modularity helps both in understanding what a program does, as well as with reusability. Global variables reduce modularity significantly.

    > **best practice**
    >
    > Use local variables instead of global variables whenever possible.

    **So what are very good reasons to use non-const global variables?**

    There aren’t many. In most cases, there are other ways to solve the problem that avoids the use of non-const global variables. But in some cases, judicious use of non-const global variables *can* actually reduce program complexity, and in these rare cases, their use may be better than the alternatives.

    **Protecting yourself from global destruction**

    https://www.learncpp.com/cpp-tutorial/why-global-variables-are-evil/

    

13. **Static local variables**

    Using the `static` keyword on a local variable changes its duration from `automatic duration` to `static duration`. This means the variable is now created at the start of the program, and destroyed at the end of the program (just like a global variable). As a result, the static variable will retain its value even after it goes out of scope!

    The easiest way to show the difference between `automatic duration` and `static duration` variables is by example.

    Automatic duration (default):

    ```c++
    #include <iostream>
     
    void incrementAndPrint()
    {
        int value{ 1 }; // automatic duration by default
        ++value;
        std::cout << value << '\n';
    } // value is destroyed here
     
    int main()
    {
        incrementAndPrint();
        incrementAndPrint();
        incrementAndPrint();
     
        return 0;
    }
    ```

    Static duration (using static keyword):

    ```c++
    #include <iostream>
     
    void incrementAndPrint()
    {
        static int s_value{ 1 }; // static duration via static keyword.  This initializer is only executed once.
        ++s_value;
        std::cout << s_value << '\n';
    } // s_value is not destroyed here, but becomes inaccessible because it goes out of scope
     
    int main()
    {
        incrementAndPrint();
        incrementAndPrint();
        incrementAndPrint();
     
        return 0;
    }
    ```

    In this program, because `s_value` has been declared as `static`, `s_value` is created and initialized once (at program start). If we were not using a constant expression to initialize `s_value`, it would be zero-initialized at program start and then initialized with our supplied initialization value the first time the variable definition is encountered (but it is not reinitialized on subsequent calls).

    Just like we use “g_” to prefix global variables, it’s common to use “s_” to prefix static (static duration) local variables.

    Static variables offer some of the benefit of global variables (they don’t get destroyed until the end of the program) while limiting their visibility to block scope. This makes them safe for use even if you change their values regularly.

    > Best practice
    >
    > Avoid `static` local variables, unless the variable never needs to be reset. `static` local variables decrease reusability and make functions harder to reason about.

    

14. **Scope summary**

    An identifier’s *scope* determines where the identifier can be accessed within the source code.

    - Variables with **block scope / local scope** can only be accessed within the block in which they are declared (including nested blocks). This includes:

    - - Local variables
      - Function parameters
      - User-defined type definitions (such as enums and classes) declared inside a block

    - Variables and functions with **global scope / file scope** can be accessed anywhere in the file. This includes:

    - - Global variables
      - Functions
      - User-defined type definitions (such as enums and classes) declared inside a namespace or in the global scope

    **Duration summary**

    A variable’s *duration* determines when it is created and destroyed.

    - Variables with **automatic duration** are created at the point of definition, and destroyed when the block they are part of is exited. This includes:

    - - Local variables
      - Function parameters

    - Variables with **static duration** are created when the program begins and destroyed when the program ends. This includes:

    - - Global variables
      - Static local variables

    - Variables with **dynamic duration** are created and destroyed by programmer request. This includes:

    - - Dynamically allocated variables

    Linkage summary

    An identifier’s *linkage* determines whether multiple declarations of an identifier refer to the same identifier or not.

    - An identifier with **no linkage** means the identifier only refers to itself. This includes:

    - - Local variables
      - User-defined type definitions (such as enums and classes) declared inside a block

    - An identifier with **internal linkage** can be accessed anywhere within the file it is declared. This includes:

    - - Static global variables (initialized or uninitialized)
      - Static functions
      - Const global variables
      - Functions declared inside an unnamed namespace
      - User-defined type definitions (such as enums and classes) declared inside an unnamed namespace

    - An identifier with **external linkage** can be accessed anywhere within the file it is declared, or other files (via a forward declaration). This includes:

    - - Functions
      - Non-const global variables (initialized or uninitialized)
      - Extern const global variables
      - Inline const global variables
      - User-defined type definitions (such as enums and classes) declared inside a namespace or in the global scope

    **Variable scope, duration, and linkage summary**

    | Type                                  | Example                         | Scope | Duration  | Linkage  | Notes                             |
    | :------------------------------------ | :------------------------------ | :---- | :-------- | :------- | :-------------------------------- |
    | Local variable                        | int x;                          | Block | Automatic | None     |                                   |
    | Static local variable                 | static int s_x;                 | Block | Static    | None     |                                   |
    | Dynamic variable                      | int *x { new int{} };           | Block | Dynamic   | None     |                                   |
    | Function parameter                    | void foo(int x)                 | Block | Automatic | None     |                                   |
    | External non-constant global variable | int g_x;                        | File  | Static    | External | Initialized or uninitialized      |
    | Internal non-constant global variable | static int g_x;                 | File  | Static    | Internal | Initialized or uninitialized      |
    | Internal constant global variable     | constexpr int g_x { 1 };        | File  | Static    | Internal | Must be initialized               |
    | External constant global variable     | extern constexpr int g_x { 1 }; | File  | Static    | External | Must be initialized               |
    | Inline constant global variable       | inline constexpr int g_x { 1 }; | File  | Static    | External | Must be initialized               |
    | Internal constant global variable     | const int g_x { 1 };            | File  | Static    | Internal | Must be initialized               |
    | External constant global variable     | extern const int g_x { 1 };     | File  | Static    | External | Must be initialized at definition |
    | Inline constant global variable       | inline const int g_x { 1 };     | File  | Static    | External | Must be initialized               |

    **Forward declaration summary**

    | Type                                             | Example                   | Notes                                             |
    | :----------------------------------------------- | :------------------------ | :------------------------------------------------ |
    | Function forward declaration                     | void foo(int x);          | Prototype only, no function body                  |
    | Non-constant global variable forward declaration | extern int g_x;           | Must be uninitialized                             |
    | Const global variable forward declaration        | extern const int g_x;     | Must be uninitialized                             |
    | Constexpr global variable forward declaration    | extern constexpr int g_x; | Not allowed, constexpr cannot be forward declared |

    **What the heck is a storage class specifier?**

    | Specifier    | Meaning                                                      | Note                |
    | :----------- | :----------------------------------------------------------- | :------------------ |
    | extern       | static (or thread_local) storage duration and external linkage |                     |
    | static       | static (or thread_local) storage duration and internal linkage |                     |
    | thread_local | thread storage duration                                      | Introduced in C++11 |
    | mutable      | object allowed to be modified even if containing class is const |                     |
    | auto         | automatic storage duration                                   | Deprecated in C++11 |
    | register     | automatic storage duration and hint to the compiler to place in a register | Deprecated in C++17 |

    The term *storage class specifier* is typically only used in formal documentation.

15. **Using declarations**

    ```c++
    #include <iostream>
     
    int main()
    {
       using std::cout; // this using declaration tells the compiler that cout should resolve to std::cout
       cout << "Hello world!"; // so no std:: prefix is needed here!
     
       return 0;
    } // the using declaration expires here
    ```

    The `using declaration` of `using std::cout;` tells the compiler that we’re going to be using the object `cout` from the `std namespace`. So whenever it sees `cout`, it will assume that we mean `std::cout`. If there’s a naming conflict between `std::cout` and some other use of `cout`, `std::cout` will be preferred. Therefore on line 6, we can type `cout` instead of `std::cout`.

    **The using directive**

    ```c++
    #include <iostream>
     
    int main()
    {
       using namespace std; // this using directive tells the compiler that we're using everything in the std namespace!
       cout << "Hello world!"; // so no std:: prefix is needed here!
       return 0;
    }
    ```

    The `using directive` `using namespace std;` tells the compiler that we want to use *everything* in the `std namespace`, so if the compiler finds a name it doesn’t recognize, it will check the `std namespace`. Consequently, when the compiler encounters `cout` (which it won’t recognize), it’ll look in the `std namespace` and find it there. If there’s a naming conflict between `std::cout` and some other use of `cout`, the compiler will flag it as an **error** (rather than preferring one instance over the other).

    ```c++
    #include <iostream>
    namespace a
    {
    	int x{ 10 };
    }
    namespace b
    {
    	int x{ 20 };
    }
    int main()
    {
    	using namespace a;
    	using namespace b;
    	std::cout << x << '\n';
    	return 0;
    }
    ```

    In the above example, the compiler is unable to determine whether the `x` in `main` refers to `a::x` or `b::x`. In this case, it will fail to compile with an “ambiguous symbol” error. We could resolve this by removing one of the `using statements`, or using an explicit `a::` or `b::` prefix with variable `x`.

    ```c++
    #include <iostream> // imports the declaration of std::cout
     
    int cout() // declares our own "cout" function
    {
        return 5;
    }
     
    int main()
    {
        using namespace std; // makes std::cout accessible as "cout"
        cout << "Hello, world!"; // uh oh!  Which cout do we want here?  The one in the std namespace or the one we defined above?
     
        return 0;
    }
    ```

    In the above example, the compiler is unable to determine whether our use of `cout` means `std::cout` or the `cout` function we’ve defined, and again will fail to compile with an “ambiguous symbol” error. Although this example is trivial, if we had explicitly prefixed `std::cout` like this:

    ```c++
    	std::cout << "Hello, world!"; // tell the compiler we mean std::cout
    ```

    or used a `using declaration` instead of a `using directive`:

    ```c++
     	using std::cout; // tell the compiler that cout means std::cout
        cout << "Hello, world!"; // so this means std::cout
    ```

    If a `using declaration` or `using directive` is used within a block, the `using statement` applies only within that block (it follows normal block scoping rules). This is a good thing, as it reduces the chances for naming collisions to occur just within that block. However, many new programmers put `using directives` into the global scope. This pulls all of the names from the namespace directly into the global scope, greatly increasing the chance for naming collisions to occur.

    > **best practice**
    >
    > Although many textbooks and tutorials use them liberally, avoid `using directives` altogether. `Using declarations` are okay to use inside blocks, where their impact is limited, but not in the global scope.

    
    
16. **Typedefs** allow the programmer to create an alias for a data type, and use the aliased name instead of the actual type name. Typedef literally stands for, “type definition”.

    By convention, `typedef` names are declared using a “_t” suffix. This helps indicate that the identifier represents a type, not a variable or function, and also helps prevent naming collisions with other identifiers.

    Note that a `typedef` does not define a new type. Rather, it is simply an alias (another name) for an existing type. A `typedef` can be used interchangeably anywhere a regular type can be used.

    `typedef`s and type aliases follow the same scoping rules as variables.

    ```c++
    typedef distance_t double; // incorrect
    typedef double distance_t; // correct
    ```

    This can be declared as the following type alias:

    ```c++
    using distance_t = double; // define distance_t as an alias for type double
    ```

    Note that although the type alias syntax uses the “using” keyword, this is an overloaded meaning, and does not have anything to do with the `using statements` related to namespaces.

    **Using type aliases for legibility**

    ```c++
    using testScore_t = int;
    testScore_t GradeTest();
    ```

    using a return type of testScore_t makes it obvious that the function is returning a type that represents a test score.

    **Using type aliases for easier code maintenance**

    Type aliases also allow you to change the underlying type of an object without having to change lots of code. For example, if you were using a `short` to hold a student’s ID number, but then later decided you needed a `long` instead, you’d have to comb through lots of code and replace `short` with `long`. It would probably be difficult to figure out which `shorts` were being used to hold ID numbers and which were being used for other purposes.

    However, with a type alias, all you have to do is change `using studentID_t = short;` to `using studentID_t = long;`. However, caution is still necessary when changing the type of a type alias to a type in a different type family (e.g. an integer to a floating point value, or vice versa)! The new type may have comparison or integer/floating point division issues, or other issues that the old type did not.

    **Using type aliases for platform independent coding**

    ```c++
    #ifdef INT_2_BYTES
    using int8_t = char;
    using int16_t = int;
    using int32_t = long;
    #else
    using int8_t = char;
    using int16_t = short;
    using int32_t = int;
    #endif
    ```

    **Using type aliases to make complex types simple**

    ```c++
    std::vector<std::pair<std::string, int> > pairlist;
     
    bool hasDuplicates(std::vector<std::pair<std::string, int> > pairlist)
    {
        // some code here
    }
    ```

    Typing `std::vector<std::pair<std::string, int> >` everywhere you need to use that type can get cumbersome. It’s much easier to use a type alias:

    ```c++
    using pairlist_t = std::vector<std::pair<std::string, int> >; // make pairlist_t an alias for this crazy type
     
    pairlist_t pairlist; // instantiate a pairlist_t variable
     
    bool hasDuplicates(pairlist_t pairlist) // use pairlist_t in a function parameter
    {
        // some code here
    }
    ```

    > **Best practice**
    >
    > Favor type aliases over typedefs, and use them liberally to document the meaning of your types.
    
    
    
17. When initializing a variable, the `auto` keyword can be used in place of the `type` to tell the compiler to infer the variable’s type from the initializer’s type. This is called **type inference** (also sometimes called **type deduction**).

    ```c++
    auto d{ 5.0 }; // 5.0 is a double literal, so d will be type double
    auto i{ 1 + 2 }; // 1 + 2 evaluates to an int, so i will be type int
    ```

    **Type inference for functions**

    In C++14, the `auto` keyword was extended to be able to deduce a function’s return type from return statements in the function body. Consider the following program:

    ```c++
    auto add(int x, int y)
    {
        return x + y;
    }
    ```

    > **best practice**
    >
    > Avoid using type inference for function return types.

    While this may seem neat, we recommend that this syntax be avoided for normal functions. The return type of a function is of great use in helping to document for the caller what a function is expected to return. When a specific type isn’t specified, the caller may misinterpret what type the function will return, which can lead to inadvertent errors.

    **Trailing return type syntax**

    The `auto` keyword can also be used to declare functions using a **trailing return syntax**, where the return type is specified after the rest of the function prototype.

    One nice thing is that it makes all of your function names line up:

    ```c++
    auto add(int x, int y) -> int;
    auto divide(double x, double y) -> double;
    auto printSomething() -> void;
    auto generateSubstring(const std::string &s, int start, int len) -> std::string;
    ```

18. The process of converting a value from one data type to another is called a **type conversion**. `Type conversions` can happen in many different cases:

    * When assigning to or initializing a variable with a value of a different data type
    * When passing a value to a function where the function parameter is of a different data type
    * When returning a value from a function where the function return type is of a different data type

    There are two basic types of `type conversion`: `implicit type conversion`, where the compiler automatically transforms one data type into another, and `explicit type conversion`, where the developer uses a casting operator to direct the conversion.

    There are two basic types of `implicit type conversion`: `promotions` and `conversions`.

    * Whenever a value from one fundamental data type is converted into a value of a larger fundamental data type from the same family, this is called a **numeric promotion** (or **widening**, though this term is usually reserved for integers). For example, an `int` can be widened into a `long`, or a `float` promoted into a `double`
    * When we convert a value from a larger type to a similar smaller type, or between different types, this is called a **numeric conversion**.

    Conversions that could cause loss of information, e.g. floating point to integer, are called **narrowing conversions**. Since information loss is generally undesirable, brace initialization doesn’t allow narrowing conversions.

    **Evaluating arithmetic expressions**

    When evaluating expressions, the compiler breaks each expression down into individual subexpressions. The arithmetic operators require their operands to be of the same type. To ensure this, the compiler uses the following rules:

    - If an operand is an integer that is narrower than an int, it undergoes integral promotion (as described above) to int or unsigned int.
    - If the operands still do not match, then the compiler finds the highest priority operand and implicitly converts the other operand to match.

    The priority of operands is as follows:

    - long double (highest)
    - double
    - float
    - unsigned long long
    - long long
    - unsigned long
    - long
    - unsigned int
    - int (lowest)

    We can see the usual arithmetic conversion take place via use of the `typeid` operator (included in the <typeinfo> header), which can be used to show the resulting type of an expression.

    ```c++
    #include <iostream>
    #include <typeinfo> // for typeid()
     
    int main()
    {
        short a{ 4 };
        short b{ 5 };
        std::cout << typeid(a + b).name() << ' ' << a + b << '\n'; // show us the type of a + b
     
        return 0;
    }
    ```

    Because `shorts` are integers, they undergo `integral promotion` to `ints` before being added. The result of adding two `ints` is an `int`, as you would expect:

    ```c++
    int 9
    ```

19. In C++, there are 5 different types of casts: `C-style casts`, `static casts`, `const casts`, `dynamic casts`, and `reinterpret casts`. The latter four are sometimes referred to as **named casts**.

    > warning
    >
    > Avoid const casts and reinterpret casts unless you have a very good reason to use them.

    **C-style casts**
    
    In standard C programming, casts are done via the () operator, with the name of the type to convert the value to placed inside the parenthesis. For example:
    
    ```c++
    int i1 { 10 };
    int i2 { 4 }; 
    float f { (float)i1 / i2 };
    ```
    
    C++ will also let you use a `C-style cast` with a more function-call like syntax:
    
    ```c++
    int i1 { 10 };
    int i2 { 4 };
    float f { float(i1) / i2 };
    ```
    
    > warning
    >
    > Avoid using C-style casts.
    
    **static_cast**
    
    The `static_cast` operator takes a single value as input, and outputs the same value converted to the type specified inside the angled brackets. `Static_cast` is best used to convert one fundamental type into another.
    
    ```c++
    int i1 { 10 };
    int i2 { 4 };
     
    // convert an int to a float so we get floating point division rather than integer division
    float f { static_cast<float>(i1) / i2 };
    ```
    
    > **Best practice**
    >
    > Favor static_cast when you need to convert a value from one type to another type
    
    **Using casts to make implicit type conversions clear**
    
    Compilers will often complain when an unsafe implicit type conversion is performed. For example, consider the following program:
    
    ```c++
    int i { 48 };
    char ch = i; // implicit conversion
    ```
    
    Casting an int (4 bytes) to a char (1 byte) is potentially unsafe (as the compiler can’t tell whether the integer will overflow the range of the char or not), and so the compiler will typically print a warning. If we used list initialization, the compiler would yield an error.
    
    To get around this, we can use a static cast to explicitly convert our integer to a char:
    
    ```c++
    int i { 48 };
     
    // explicit conversion from int to char, so that a char is assigned to variable ch
    char ch { static_cast<char>(i) };
    ```
    
20. **Unnamed (anonymous) namespaces**

    An **unnamed namespace** (also called an **anonymous namespace**) is a namespace that is defined without a name, like so:

    ```c++
    #include <iostream>
     
    namespace // unnamed namespace
    {
        void doSomething() // can only be accessed in this file
        {
            std::cout << "v1\n";
        }
    }
     
    int main()
    {
        doSomething(); // we can call doSomething() without a namespace prefix
     
        return 0;
    }
    ```

    This prints:

    ```c++
    v1
    ```

##  Compound Types

1. **String input and output**

   Strings can be output as expected using std::cout

   However, using strings with std::cin may yield some surprises! Consider the following example:

   ```c++
   #include <iostream>
   #include <string>
    
   int main()
   {
       std::cout << "Enter your full name: ";
       std::string name{};
       std::cin >> name; // this won't work as expected since std::cin breaks on whitespace
    
       std::cout << "Enter your age: ";
       std::string age{};
       std::cin >> age;
    
       std::cout << "Your name is " << name << " and your age is " << age << '\n';
    
       return 0;
   }
   ```

   Here’s the results from a sample run of this program:

   ```c++
   Enter your full name: John Doe
   Enter your age: Your name is John and your age is Doe
   ```

   **Use std::getline() to input text**

   To read a full line of input into a string, you’re better off using the std::getline() function instead. std::getline() takes two parameters: the first is std::cin, and the second is your string variable.

   ```c++
   #include <string> // For std::string and std::getline
   #include <iostream>
    
   int main()
   {
       std::cout << "Enter your full name: ";
       std::string name{};
       std::getline(std::cin, name); // read a full line of text into name
    
       std::cout << "Enter your age: ";
       std::string age{};
       std::getline(std::cin, age); // read a full line of text into age
    
       std::cout << "Your name is " << name << " and your age is " << age << '\n';
    
       return 0;
   }
   ```

   Now our program works as expected

   **Mixing std::cin and std::getline()**

   Reading inputs with both std::cin and std::getline may cause some unexpected behavior. Consider the following:

   ```c++
   #include <string>
   #include <iostream>
    
   int main()
   {
       std::cout << "Pick 1 or 2: ";
       int choice{};
       std::cin >> choice;
    
       std::cout << "Now enter your name: ";
       std::string name{};
       std::getline(std::cin, name);
    
       std::cout << "Hello, " << name << ", you picked " << choice << '\n';
    
       return 0;
   }
   ```

   This program first asks you to enter 1 or 2, and waits for you to do so. All good so far. Then it will ask you to enter your name. However, it won’t actually wait for you to enter your name! Instead, it prints the “Hello” line, and then exits. What happened?

   It turns out, when you enter a value using cin, cin not only captures the value, it also captures the newline. So when we enter 2, cin actually gets the string “2\n”. It then extracts the 2 to variable choice, leaving the newline stuck in the input stream. Then, when std::getline() goes to read the name, it sees “\n” is already in the stream, and figures we must have entered an empty string! Definitely not what was intended.

   A good rule of thumb is that after reading a value with std::cin, remove the newline from the stream. This can be done using the following:

   ```c++
   std::cin.ignore(32767, '\n'); // ignore up to 32767 characters until a \n is removed
   ```

   If we insert this line directly after reading variable choice, the extraneous newline will be removed from the stream, and the program will work as expected!

   ```c++
   #include <iostream>
   #include <string>
    
   int main()
   {
   	std::cout << "Pick 1 or 2: ";
   	int choice{};
   	std::cin >> choice;
    
   	std::cin.ignore(32767, '\n'); // ignore up to 32767 characters until a \n is removed
    
   	std::cout << "Now enter your name: ";
   	std::string name{};
   	std::getline(std::cin, name);
    
   	std::cout << "Hello, " << name << ", you picked " << choice << '\n';
    
   	return 0;
   }
   ```

   > **Rule**
   >
   > If reading values with std::cin, it’s a good idea to remove the extraneous newline using std::cin.ignore().

   

   **What’s that 32767 magic number in your code?**

   That tells std::cin.ignore() how many characters to ignore up to. We picked that number because it’s the largest signed value guaranteed to fit in a (2-byte) integer on all platforms.

   Technically, the correct way to ignore an unlimited amount of input is as follows:

   ```c++
   #include <limits>
    
   ...
    
   std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n'); // ignore unlimited characters until a \n is removed
   ```

   **Appending strings**

   You can use operator+ to concatenate two strings together (returning a new string), or operator+= to append a string to the end of an existing string).

   **String length**

   ```c++
   myName.length()
   ```

   The length function isn’t a normal standalone function like we’ve used up to this point -- it’s a special type of function that belongs to std::string called a member function. 

2.  An **enumerated type** (also called an **enumeration** or **enum**) is a data type where every possible value is defined as a symbolic constant (called an **enumerator**). Enumerations are defined via the **enum** keyword. Let’s look at an example:

   ```c++
   // Define a new enumeration named Color
   enum Color
   {
       // Here are the enumerators
       // These define all the possible values this type can hold
       // Each enumerator is separated by a comma, not a semicolon
       COLOR_BLACK,
       COLOR_RED,
       COLOR_BLUE,
       COLOR_GREEN,
       COLOR_WHITE,
       COLOR_CYAN,
       COLOR_YELLOW,
       COLOR_MAGENTA, // see note about trailing comma on the last enumerator below
   }; // however the enum itself must end with a semicolon
    
   // Define a few variables of enumerated type Color
   Color paint = COLOR_WHITE;
   Color house(COLOR_BLUE);
   Color apple { COLOR_RED };
   ```

   Defining an enumeration (or any user-defined data type) does not allocate any memory. When a variable of the enumerated type is defined (such as variable paint in the example above), memory is allocated for that variable at that time.

   Note that each enumerator is separated by a comma, and the entire enumeration is ended with a semicolon.

   Prior to C++11, a trailing comma after the last enumerator (e.g. after COLOR_MAGENTA) is not allowed (though many compilers accepted it anyway). However, starting with C++11, a trailing comma is allowed. Now that C++11 compilers are more prevalent, use of a trailing comma after the last element is generally considered acceptable.

   **Enumerator scope**

   Because enumerators are placed into the same namespace as the enumeration, an enumerator name can’t be used in multiple enumerations within the same namespace:

   **Enumerator values**

   ```c++
   enum Color
   {
       COLOR_BLACK, // assigned 0
       COLOR_RED, // assigned 1
       COLOR_BLUE, // assigned 2
       COLOR_GREEN, // assigned 3
       COLOR_WHITE, // assigned 4
       COLOR_CYAN, // assigned 5
       COLOR_YELLOW, // assigned 6
       COLOR_MAGENTA // assigned 7
   };
    
   Color paint(COLOR_WHITE);
   std::cout << paint;
   ```

   The cout statement above prints the value 4.

   It is possible to explicitly define the value of enumerator. These integer values can be positive or negative and can share the same value as other enumerators. Any non-defined enumerators are given a value one greater than the previous enumerator.

   ```c++
   // define a new enum named Animal
   enum Animal
   {
       ANIMAL_CAT = -3,
       ANIMAL_DOG, // assigned -2
       ANIMAL_PIG, // assigned -1
       ANIMAL_HORSE = 5,
       ANIMAL_GIRAFFE = 5, // shares same value as ANIMAL_HORSE
       ANIMAL_CHICKEN // assigned 6
   };
   ```

   > **Best practice**
   >
   > Don’t assign specific values to your enumerators.
   >
   > **Rule**
   >
   > Don’t assign the same value to two enumerators in the same enumeration unless there’s a very good reason.

   **Enum type evaluation and input/output**
   
   **What are enumerators useful for?**
   
   Enumerated types are best used when defining a set of related identifiers. For example, let’s say you were writing a game where the player can carry one item, but that item can be several different types. You could do this:
   
   ```c++
   #include <iostream>
   #include <string>
    
   enum ItemType
   {
       ITEMTYPE_SWORD,
       ITEMTYPE_TORCH,
       ITEMTYPE_POTION
   };
    
   std::string getItemName(ItemType itemType)
   {
       if (itemType == ITEMTYPE_SWORD)
           return "Sword";
       if (itemType == ITEMTYPE_TORCH)
           return "Torch";
       if (itemType == ITEMTYPE_POTION)
           return "Potion";
    
       // Just in case we add a new item in the future and forget to update this function
       return "???";
   }
    
   int main()
   {
       // ItemType is the enumerated type we've defined above.
       // itemType (lower case i) is the name of the variable we're defining (of type ItemType).
       // ITEMTYPE_TORCH is the enumerated value we're initializing variable itemType with.
       ItemType itemType{ ITEMTYPE_TORCH };
    
       std::cout << "You are carrying a " << getItemName(itemType) << '\n';
    
       return 0;
   }
   ```
   
3. C++11 defines a new concept, the **enum class** (also called a **scoped enumeration**), which makes enumerations both strongly typed and strongly scoped. To make an enum class, we use the keyword **class** after the enum keyword. Here’s an example:

   ```c++
   #include <iostream>
    
   int main()
   {
       enum class Color // "enum class" defines this as a scoped enumeration instead of a standard enumeration
       {
           red, // red is inside the scope of Color
           blue
       };
    
       enum class Fruit
       {
           banana, // banana is inside the scope of Fruit
           apple
       };
    
       Color color{ Color::red }; // note: red is not directly accessible any more, we have to use Color::red
       Fruit fruit{ Fruit::banana }; // note: banana is not directly accessible any more, we have to use Fruit::banana
   	
       if (color == fruit) // compile error here, as the compiler doesn't know how to compare different types Color and Fruit
           std::cout << "color and fruit are equal\n";
       else
           std::cout << "color and fruit are not equal\n";
    
       return 0;
   }
   ```

   The strong typing rules means that each enum class is considered a unique type. This means that the compiler will *not* implicitly compare enumerators from different enumerations. If you try to do so, the compiler will throw an error, as shown in the example above.

   However, note that you can still compare enumerators from within the same enum class (since they are of the same type):

   ```c++
   #include <iostream>
    
   int main()
   {
       enum class Color
       {
           red,
           blue
       };
    
       Color color{ Color::red };
    
       if (color == Color::red) // this is okay
           std::cout << "The color is red!\n";
       else if (color == Color::blue)
           std::cout << "The color is blue!\n";
    
       return 0;
   }
   ```

   With enum classes, the compiler will no longer implicitly convert enumerator values to integers. This is mostly a good thing. However, there are occasionally cases where it is useful to be able to do so. In these cases, you can explicitly convert an enum class enumerator to an integer by using a static_cast to int:

   ```c++
   #include <iostream>
    
   int main()
   {
       enum class Color
       {
           red,
           blue
       };
    
       Color color{ Color::blue };
    
       std::cout << color; // won't work, because there's no implicit conversion to int
       std::cout << static_cast<int>(color); // will print 1
    
       return 0;
   }
   ```

4. Initializing structs by assigning values member by member is a little cumbersome, so C++ supports a faster way to initialize structs using an **initializer list**. 

   ```c++
   struct Employee
   {
       short id;
       int age;
       double wage;
   };
    
   Employee joe{ 1, 32, 60000.0 }; // joe.id = 1, joe.age = 32, joe.wage = 60000.0
   Employee frank{ 2, 28 }; // frank.id = 2, frank.age = 28, frank.wage = 0.0 (default initialization)
   ```



1. A **pseudo-random number generator (PRNG)** is a program that takes a starting number (called a **seed**), and performs mathematical operations on it to transform it into some other number that appears to be unrelated to the seed. It then takes that generated number and performs the same mathematical operation on it to transform it into a new number that appears unrelated to the number it was generated from. By continually applying the algorithm to the last generated number, it can generate a series of new numbers that will appear to be random if the algorithm is complex enough.

   > **Rule**
   >
   > You should only seed your random number generators once. Seeding them more than once will cause the results to be less random or not random at all.

   **Generating random numbers in C++**

   C (and by extension C++) comes with a built-in pseudo-random number generator. It is implemented as two separate functions that live in the cstdlib header:

   `std::srand()` sets the initial seed value to a value that is passed in by the caller. std::srand() should only be called once at the beginning of your program. This is usually done at the top of main().

   `std::rand()` generates the next random number in the sequence. That number will be a pseudo-random integer between 0 and RAND_MAX, a constant in cstdlib that is typically set to 32767.

   Here’s a sample program using these functions:

   ```c++
   #include <iostream>
   #include <cstdlib> // for std::rand() and std::srand()
    
   int main()
   {
       std::srand(5323); // set initial seed value to 5323
    
       // Print 100 random numbers
       for (int count{ 1 }; count <= 100; ++count)
       {
           std::cout << std::rand() << '\t';
    
           // If we've printed 5 numbers, start a new row
           if (count % 5 == 0)
               std::cout << '\n';
   	}
    
       return 0;
   
   ```

   C comes with a function called std::time() that returns the number of seconds since midnight on Jan 1, 1970. To use it, we merely need to include the ctime header, and then initialize std::srand() with a call to std::time(nullptr). We haven’t covered *nullptr* yet, but it’s essentially the equivalent of 0 in this context.

   Here’s the same program as above, using a call to time() as the seed:

   ```c++
   #include <iostream>
   #include <cstdlib> // for std::rand() and std::srand()
   #include <ctime> // for std::time()
    
   int main()
   {
       std::srand(static_cast<unsigned int>(std::time(nullptr))); // set initial seed value to system clock
    
       for (int count{ 1 }; count <= 100; ++count)
       {
           std::cout << std::rand() << '\t';
    
           // If we've printed 5 numbers, start a new row
           if (count % 5 == 0)
               std::cout << '\n';
   	}
    
       return 0;
   }
   ```

   **Generating random numbers between two arbitrary values**\

   Generally, we do not want random numbers between 0 and RAND_MAX -- we want numbers between two other values, which we’ll call min and max. For example, if we’re trying to simulate the user rolling a die, we want random numbers between 1 and 6 (pedantic grammar note: yes, die is the singular of dice).

   Here’s a short function that converts the result of rand() into the range we want:

   ```c++
   // Generate a random number between min and max (inclusive)
   // Assumes std::srand() has already been called
   // Assumes max - min <= RAND_MAX
   int getRandomNumber(int min, int max)
   {
       static constexpr double fraction { 1.0 / (RAND_MAX + 1.0) };  // static used for efficiency, so we only calculate this value once
       // evenly distribute the random number across our range
       return min + static_cast<int>((max - min + 1) * (std::rand() * fraction));
   }
   ```

   **Optional reading: Why don’t we use the modulus operator (%) in the previous function?**

   The short answer is that the modulus method tends to be biased in favor of low numbers.

   **What is a good PRNG?**

   In order to be a good PRNG, the PRNG needs to exhibit a number of properties:

   First, the PRNG should generate each number with approximately the same probability. This is called distribution uniformity. If some numbers are generated more often than others, the result of the program that uses the PRNG will be biased!

   For example, let’s say you’re trying to write a random item generator for a game. You’ll pick a random number between 1 and 10, and if the result is a 10, the monster will drop a powerful item instead of a common one. You would expect a 1 in 10 chance of this happening. But if the underlying PRNG is not uniform, and generates a lot more 10s than it should, your players will end up getting more rare items than you’d intended, possibly trivializing the difficulty of your game.

   Generating PRNGs that produce uniform results is difficult, and it’s one of the main reasons the PRNG we wrote at the top of this lesson isn’t a very good PRNG.

   Second, the method by which the next number in the sequence is generated shouldn’t be obvious or predictable. For example, consider the following PRNG algorithm: `num = num + 1`. This PRNG is perfectly uniform, but it’s not very useful as a sequence of random numbers!

   Third, the PRNG should have a good dimensional distribution of numbers. This means it should return low numbers, middle numbers, and high numbers seemingly at random. A PRNG that returned all low numbers, then all high numbers may be uniform and non-predictable, but it’s still going to lead to biased results, particularly if the number of random numbers you actually use is small.

   Fourth, all PRNGs are periodic, which means that at some point the sequence of numbers generated will begin to repeat itself. The length of the sequence before a PRNG begins to repeat itself is known as the **period**.

   This happens because PRNGs are deterministic -- given some set of input values, they will produce the same output value every time. This means that once the PRNG encounters a set of inputs it has used before, it will start producing the same sequence of outputs it has produced before -- resulting in a loop.

   A good PRNG should have a long period for *all* seed numbers. Designing an algorithm that meets this property can be extremely difficult -- most PRNGs will have long periods for some seeds and short periods for others. If the user happens to pick a seed that has a short period, then the PRNG won’t be doing a good job.

   Despite the difficulty in designing algorithms that meet all of these criteria, a lot of research has been done in this area because of its importance to scientific computing.

   **std::rand() is a mediocre PRNG**

   Most implementations of rand() use a method called a [Linear Congruential Generator (LCG)](http://en.wikipedia.org/wiki/Linear_congruential_generator).

   For applications where a high-quality PRNG is useful, I would recommend [Mersenne Twister](http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/emt.html) (or one of its variants), which produces great results and is relatively easy to use. Mersenne Twister was adopted into C++11, and we’ll show how to use it later in this lesson.

   **Better random numbers using Mersenne Twister**

   C++11 added a ton of random number generation functionality to the C++ standard library, including the Mersenne Twister algorithm, as well as generators for different kinds of random distributions (uniform, normal, Poisson, etc…). This is accessed via the <random> header.

   Here’s a short example showing how to generate random numbers in C++11 using Mersenne Twister (h/t to user Fernando):

   ```c++
   #include <iostream>
   #include <random> // for std::mt19937
   #include <ctime> // for std::time
    
   int main()
   {
   	// Initialize our mersenne twister with a random seed based on the clock
   	std::mt19937 mersenne{ static_cast<std::mt19937::result_type>(std::time(nullptr)) };
    
   	// Create a reusable random number generator that generates uniform numbers between 1 and 6
   	std::uniform_int_distribution die{ 1, 6 };
   	// If your compiler doesn't support C++17, use this instead
   	// std::uniform_int_distribution<> die{ 1, 6 };
    
   	// Print a bunch of random numbers
   	for (int count{ 1 }; count <= 48; ++count)
   	{
   		std::cout << die(mersenne) << '\t'; // generate a roll of the die here
    
   		// If we've printed 6 numbers, start a new row
   		if (count % 6 == 0)
   			std::cout << '\n';
   	}
    
   	return 0;
   }
   ```

   > **Author's note**
   >
   > Before C++17, you need to add empty brackets to create `die` after the type
   > `std::uniform_int_distribution<> die{ 1, 6 }`
   
   **Random numbers across multiple functions**
   
   Although you can create a static local std::mt19937 variable in each function that needs it (static so that it only gets seeded once), it’s a little overkill to have every function that needs a random number generator seed and maintain its own local generator. A better option in most cases is to create a global random number generator (inside a namespace!). Remember how we told you to avoid non-const global variables? This is an exception (also note: std::rand() and std::srand() access a global object, so there’s precedent for this).
   
   ```c++
   #include <iostream>
   #include <random> // for std::mt19937
   #include <ctime> // for std::time
    
   namespace MyRandom
   {
   	// Initialize our mersenne twister with a random seed based on the clock (once at system startup)
   	std::mt19937 mersenne{ static_cast<std::mt19937::result_type>(std::time(nullptr)) };
   }
    
   int getRandomNumber(int min, int max)
   {
   	std::uniform_int_distribution die{ min, max }; // we can create a distribution in any function that needs it
   	return die(MyRandom::mersenne); // and then generate a random number from our global generator
   }
    
   int main()
   {
   	std::cout << getRandomNumber(1, 6) << '\n';
   	std::cout << getRandomNumber(1, 10) << '\n';
   	std::cout << getRandomNumber(1, 20) << '\n';
    
   	return 0;
   }
   ```
   
   **Using a random library**
   
   A perhaps better solution is to use a 3rd party library that handles all of this stuff for you, such as the header-only [Effolkronium’s random library](https://github.com/effolkronium/random). You simply add the header to your project, #include it, and then you can start generating random numbers via `Random::get(min, max)`.
   
2. **std::cin, buffers, and extraction**

   When we use operator>> to get user input and put it into a variable, this is called an “extraction”. The >> operator is accordingly called the extraction operator when used in this context.

   When the user enters input in response to an extraction operation, that data is placed in a buffer inside of std::cin. A **buffer** (also called a data buffer) is simply a piece of memory set aside for storing data temporarily while it’s moved from one place to another. In this case, the buffer is used to hold user input while it’s waiting to be extracted to variables.

   When the extraction operator is used, the following procedure happens:

   - If there is data already in the input buffer, that data is used for extraction.
   - If the input buffer contains no data, the user is asked to input data for extraction (this is the case most of the time). When the user hits enter, a ‘\n’ character will be placed in the input buffer.
   - operator>> extracts as much data from the input buffer as it can into the variable (ignoring any leading whitespace characters, such as spaces, tabs, or ‘\n’).
   - Any data that can not be extracted is left in the input buffer for the next extraction.
   
3. **std::cin, buffers, and extraction**

   In order to discuss how std::cin and operator>> can fail, it first helps to know a little bit about how they work.

   When we use operator>> to get user input and put it into a variable, this is called an “extraction”. The >> operator is accordingly called the extraction operator when used in this context.

   When the user enters input in response to an extraction operation, that data is placed in a buffer inside of std::cin. A **buffer** (also called a data buffer) is simply a piece of memory set aside for storing data temporarily while it’s moved from one place to another. In this case, the buffer is used to hold user input while it’s waiting to be extracted to variables.

   When the extraction operator is used, the following procedure happens:

   - If there is data already in the input buffer, that data is used for extraction.
   - If the input buffer contains no data, the user is asked to input data for extraction (this is the case most of the time). When the user hits enter, a ‘\n’ character will be placed in the input buffer.
   - operator>> extracts as much data from the input buffer as it can into the variable (ignoring any leading whitespace characters, such as spaces, tabs, or ‘\n’).
   - Any data that can not be extracted is left in the input buffer for the next extraction.

   Extraction succeeds if at least one character is extracted from the input buffer. Any unextracted input is left in the input buffer for future extractions. For example:

   ```c++
   int x{};std::cin >> x;
   ```

   If the user enters “5a”, 5 will be extracted, converted to an integer, and assigned to variable x. “a\n” will be left in the input stream for the next extraction.

   Extraction fails if the input data does not match the type of the variable being extracted to. For example:

   ```c++
   int x{};std::cin >> x;
   ```

   If the user were to enter ‘b’, extraction would fail because ‘b’ can not be extracted to an integer variable.

   **Types of invalid text input**

   We can generally separate input text errors into four types:

   - Input extraction succeeds but the input is meaningless to the program (e.g. entering ‘k’ as your mathematical operator).
   - Input extraction succeeds but the user enters additional input (e.g. entering ‘*q hello’ as your mathematical operator).
   - Input extraction fails (e.g. trying to enter ‘q’ into a numeric input).
   - Input extraction succeeds but the user overflows a numeric value.

   Thus, to make our programs robust, whenever we ask the user for input, we ideally should determine whether each of the above can possibly occur, and if so, write code to handle those cases
   
   **Conclusion**
   
   As you write your programs, consider how users will misuse your program, especially around text input. For each point of text input, consider:
   
   - Could extraction fail?
   - Could the user enter more input than expected?
   - Could the user enter meaningless input?
   - Could the user overflow an input?
   
   You can use if statements and boolean logic to test whether input is expected and meaningful.
   
   ```c++
   if (std::cin.fail()) // has a previous extraction failed or overflowed?
   {
       // yep, so let's handle the failure
       std::cin.clear(); // put us back in 'normal' operation mode
       std::cin.ignore(32767,'\n'); // and remove the bad input
   }
   ```
   
   The following will also clear any extraneous input:
   
   ```c++
   std::cin.ignore(32767,'\n'); // and remove the bad input
   ```
   
4. **How to test your code: Informal testing**

   **Testing tip #1: Write your program in small, well defined units (functions), and compile often along the way**

   **Testing tip #2: Aim for 100% statement coverage**

   **Testing tip 3: Aim for 100% branch coverage**
   
   **Testing tip #4: Aim for 100% loop coverage**
   
   **Testing tip #5: Ensure you’re testing different categories of input**
   
   **How to test your code: Preserving your tests**
   
   Although writing tests and erasing them is good enough for quick and temporary testing, for code that you expect to be reusing or modifying in the future, it might make more sense to preserve your tests so they can be run again in the future. For example, instead of erasing your temporary test code, you could move it into a test() function:
   
   ```c++
   #include <iostream>
    
   bool isLowerVowel(char c)
   {
       switch (c)
       {
       case 'a':
       case 'e':
       case 'i':
       case 'o':
       case 'u':
           return true;
       default:
           return false;
       }
   }
    
   // not called from anywhere right now
   // but here if you want to retest things later
   void test()
   {
       std::cout << isLowerVowel('a'); // temporary test code, should produce 1
       std::cout << isLowerVowel('q'); // temporary test code, should produce 0
   }
    
   int main()
   {
       return 0;
   }
   ```
   
   **How to test your code: Automating your test functions**
   
   One problem with the above test function is that it relies on you to manually verify the results when you run it. We can do better by writing a function that contains both the tests AND the expected answers.
   
   ```c++
   #include <iostream>
    
   bool isLowerVowel(char c)
   {
       switch (c)
       {
       case 'a':
       case 'e':
       case 'i':
       case 'o':
       case 'u':
           return true;
       default:
           return false;
       }
   }
    
   // returns the number of the test that failed, or 0 if all tests passed
   int test()
   {
       if (isLowerVowel('a') != true) return 1;
       if (isLowerVowel('q') != false) return 2;
    
       return 0;
   }
    
   int main()
   {
       return 0;
   }
   ```
   

## Arrays, Strings, Pointers, and References

1. **Introducing std::string_view**

   C++17 introduces another way of using strings, `std::string_view`, which lives in the <string_view> header.

   Unlike `std::string`, which keeps its own copy of the string, `std::string_view` provides a *view* of a string that is defined elsewhere.

   ```c++
   #include <iostream>
   #include <string_view>
    
   int main()
   {
     std::string_view text{ "hello" }; // view the text "hello", which is stored in the binary
     std::string_view str{ text }; // view of the same "hello"
     std::string_view more{ str }; // view of the same "hello"
    
     std::cout << text << ' ' << str << ' ' << more << '\n';
    
     return 0;
   
   ```

   The output is the same, but no more copies of the string “hello” are created. When we copy a `std::string_view`, the new `std::string_view` observes the same string as the copied-from `std::string_view` is observing.
   `std::string_view` is not only fast, but has many of the functions that we know from `std::string`.

   ```c++
   #include <iostream>
   #include <string_view>
    
   int main()
   {
     std::string_view str{ "Trains are fast!" };
    
     std::cout << str.length() << '\n'; // 16
     std::cout << str.substr(0, str.find(' ')) << '\n'; // Trains
     std::cout << (str == "Trains are fast!") << '\n'; // 1
    
     // Since C++20
     std::cout << str.starts_with("Boats") << '\n'; // 0
     std::cout << str.ends_with("fast!") << '\n'; // 1
    
     std::cout << str << '\n'; // Trains are fast!
    
     return 0;
   }
   ```

   Because `std::string_view` doesn’t create a copy of the string, if we change the viewed string, the changes are reflected in the `std::string_view`.

   > **Best practice**
   >
   > Use `std::string_view` instead of C-style strings.
   >
   > Prefer `std::string_view` over `std::string` for read-only strings, unless you already have a `std::string`.

   **View modification functions**

   The functions for this are `remove_prefix`, which removes characters from the left side of the view, and `remove_suffix`, which removes characters from the right side of the view.

   **std::string_view works with non-null-terminated strings**

   Unlike C-style strings and `std::string`, `std::string_view` doesn’t use null terminators to mark the end of the string. Rather, it knows where the string ends because it keeps track of its length.

   > **Warning**
   >
   > Make sure that the underlying string viewed with a `std::string_view` does not go out of scope and isn’t modified while using the std::string_view.

2. **Dangling pointers**

   C++ does not make any guarantees about what will happen to the contents of deallocated memory, or to the value of the pointer being deleted. In most cases, the memory returned to the operating system will contain the same values it had before it was returned, and the pointer will be left pointing to the now deallocated memory.

   A pointer that is pointing to deallocated memory is called a **dangling pointer**. Dereferencing or deleting a dangling pointer will lead to undefined behavior. Consider the following program:

   ```c++
   #include <iostream>
    
   int main()
   {
       int *ptr{ new int }; // dynamically allocate an integer
       *ptr = 7; // put a value in that memory location
    
       delete ptr; // return the memory to the operating system.  ptr is now a dangling pointer.
    
       std::cout << *ptr; // Dereferencing a dangling pointer will cause undefined behavior
       delete ptr; // trying to deallocate the memory again will also lead to undefined behavior.
    
       return 0;
   }
   ```

   In the above program, the value of 7 that was previously assigned to the allocated memory will probably still be there, but it’s possible that the value at that memory address could have changed. It’s also possible the memory could be allocated to another application (or for the operating system’s own usage), and trying to access that memory will cause the operating system to shut the program down.

   Deallocating memory may create multiple dangling pointers. Consider the following example:

   ```c++
   #include <iostream>
    
   int main()
   {
       int *ptr{ new int{} }; // dynamically allocate an integer
       int *otherPtr{ ptr }; // otherPtr is now pointed at that same memory location
    
       delete ptr; // return the memory to the operating system.  ptr and otherPtr are now dangling pointers.
       ptr = nullptr; // ptr is now a nullptr
    
       // however, otherPtr is still a dangling pointer!
    
       return 0;
   }
   ```

   There are a few best practices that can help here.

   First, try to avoid having multiple pointers point at the same piece of dynamic memory. If this is not possible, be clear about which pointer “owns” the memory (and is responsible for deleting it) and which are just accessing it.

   Second, when you delete a pointer, if that pointer is not going out of scope immediately afterward, set the pointer to 0 (or nullptr in C++11). We’ll talk more about null pointers, and why they are useful in a bit.

   > *Rule: Set deleted pointers to 0 (or nullptr in C++11) unless they are going out of scope immediately afterward.*

   **Operator new can fail**

   ```c++
   int *value = new (std::nothrow) int; // value will be set to a null pointer if the integer allocation fails
   ```

   In the above example, if new fails to allocate memory, it will return a null pointer instead of the address of the allocated memory.

3. For-each loops

   The *for-each* statement has a syntax that looks like this:

   ```c++
   for (element_declaration : array)
      statement;
   ```

   ```c++
   std::string array[]{ "peter", "likes", "frozen", "yogurt" };
       for (const auto &element: array) // element is a const reference to the currently iterated array element
       {
           std::cout << element << ' ';
       }
   ```

   > **Rule**
   >
   > In for-each loops element declarations, if your elements are non-fundamental types, use references or `const` references for performance reasons.

4. **void pointer**

   A void pointer can point to objects of any data type:

   However, because the void pointer does not know what type of object it is pointing to, it cannot be dereferenced directly! Rather, the void pointer must first be explicitly cast to another pointer type before it is dereferenced.

   ```c++
   int value{ 5 };
   void *voidPtr{ &value };
    
   // std::cout << *voidPtr << '\n'; // illegal: cannot dereference a void pointer
    
   int *intPtr{ static_cast<int*>(voidPtr) }; // however, if we cast our void pointer to an int pointer...
    
   std::cout << *intPtr << '\n'; // then we can dereference it like normal
   ```

5. **Iterators**

   An **iterator** is an object designed to traverse through a container (e.g. the values in an array, or the characters in a string), providing access to each element along the way.

   **Standard library iterators**

   Iterating is such a common operation that all standard library containers offer direct support for iteration. Instead of calculating our own begin and end points, we can simply ask the container for the begin and end points via functions conveniently named `begin()` and `end()`:

   ```c++
   #include <array>
   #include <iostream>
    
   int main()
   {
     std::array array{ 1, 2, 3 };
    
     // Ask our array for the begin and end points (via the begin and end member functions).
     auto begin{ array.begin() };
     auto end{ array.end() };
    
     for (auto p{ begin }; p != end; ++p) // ++ to move to next element.
     {
       std::cout << *p << ' '; // dereference to get value of current element.
     }
     std::cout << '\n';
    
     return 0;
   }
   ```

   

6. Null values and null pointers

   Just like normal variables, pointers are not initialized when they are instantiated. Unless a value is assigned, a pointer will point to some garbage address by default.

   Besides memory addresses, there is one additional value that a pointer can hold: a null value. A **null value** is a special value that means the pointer is not pointing at anything. A pointer holding a null value is called a **null pointer**.

   In C++, we can assign a pointer a null value by initializing or assigning it the literal 0:

   ```c++
   float *ptr { 0 };  // ptr is now a null pointer
    
   float *ptr2; // ptr2 is uninitialized
   ptr2 = 0; // ptr2 is now a null pointer
   ```

   > **Best practice**
   >
   > Initialize your pointers to a null value if you’re not giving them another value.

   > **Rule**
   >
   > 
   >
   > Because NULL is a preprocessor macro with an implementation defined value, avoid using NULL.

   **The perils of using 0 (or NULL) for null pointers**

   Note that the value of 0 isn’t a pointer type, so assigning 0 (or NULL, pre-C++11) to a pointer to denote that the pointer is a null pointer is a little inconsistent. In rare cases, when used as a literal argument, it can even cause problems because the compiler can’t tell whether we mean a null pointer or the integer 0

   **nullptr in C++11**

   To address the above issues, C++11 introduces a new keyword called **nullptr**. nullptr is a keyword, much like the boolean keywords true and false are.

   Starting with C++11, this should be favored instead of 0 when we want a null pointer:

   ```c++
   int *ptr { nullptr }; // note: ptr is still an integer pointer, just set to a null value
   ```

   C++ will implicitly convert nullptr to any pointer type. So in the above example, nullptr is implicitly converted to an integer pointer, and then the value of nullptr assigned to ptr. This has the effect of making integer pointer ptr a null pointer.

   > **Best practice**
   >
   > Use nullptr to initialize your pointers to a null value.

   

   

   

   

