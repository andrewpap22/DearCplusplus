# This will be our beautiful journey into diving to the magic of C++

But first.. `let me take a selfie 🤳`. 

Ok, no... 

But first, why use C++? 

> The biggest reason for using C++ is the direct control over the computer hardware. 

So, how C++ works? 

 1. We write our code into C++
 2. We pass it over to our compiler 
 3. The compiler will output machine code translated from the C++ code to our targeted platform

> Machine code are the actual instructions that the cpu itself will follow and perform. So by using C++ we can control every single instruction that our CPU executes. 

But why and how C++ differs for example from C# or Java and why everyone says that it's faster? 

Well C# or Java differ from C++ because they run on a virtual machine. What does that mean? 
This means that our code gets compiled into an intermediate language first, and then when we actually run our application on that target platform, the VM (virtual machine) will basically convert it into machine code at run time! 

But why does that make C# or Java actually slower than C++? 

Well let's give an example here. 

Imagine that you are Greek and you want to buy a book written in Greek language so you can read it, but instead you are in a book store that only sells English written books, but you don't know any English at all, so the book store also gives you alongside the book a "live" translator. So when you get home to read the book, basically the translator reads the book in English but translates it in real time as he reads it into Greek for you to understand it. But of course you can imagine that, that is not as efficient as if the book was originally in Greek sold in a Greek book store so you could take it and immediately read it yourself in the language that you understand without a need for a translator. 

Well that's the difference between C# or Java and C++ and why C++ is closer to the hardware and faster than those other 2 languages. (We're currently talking about languages that have to be compiled and not for interpretted languages.) 

C++ can be directly translated into machine code via the compiler for the CPU to understand, while C# or Java need to first be translated into an "intermediate" language and then that "intermediate" language will have to be translated into machine code on run time from the VM compiler. 

See the extra step here? Good. 

So let's dive into the magic of C++

## 🧰 How C++ Works! 
 
So, How we go from the source file (i.e. the actualy text .cpp file) to the binary executable i.e. the program that we can run. 

### Basic Workflow of writting a C++ program: 

We have a series of source files, to which we write actual text in, and then we pass it through a compiler which compiles it to some kind of binary. Now, that binary can be some sort of library or it can be an actual executable program. 

For now we're going to talk about executable programs, a.k.a executable binaries. 

Now, let's say we have the following C++ code on a `Main.cpp` file

```c++
#include <iostream>

int main()
{
	std::cout << "Hello World!" << std::endl;
	std::cin.get();
}
```

So, in the above little program we have a couple of things going on that we can explain in more detail: 

1. `#include <iostream>` 

This is something called: a preproccessor statement. Anything that begins with a `#` is a preproccessor statement. The first thing that compiler does when it recieves our source file, is to preproccess our preproccessor statements. That's why they're called preproccessor statements because they do hapen before the actualy compilation.

In our case we have a look at the `#include`. What this statement does is to look for a file, in our case a file called `iostream` take all the contents of that file and simply copy and paste it to our current file. In our case the `Main.cpp` file. That's all it does, literally copy pasting the contents of the iostream file to our Main.cpp file. 

The reason we're including something called `iostream` is because we need a declaration for a function called `cout` which let's us print stuff to the console. 

Next up we have the `main()` function. Now, the main() function is really important. Every C++ program has a main() function. 

The main() function is called `the entry point` of our program. It's the entry point for our application. What does that mean? 

That means that when we run our application, our computer starts executing code that begins inside this function. In our example above the first thing that it will execute is the following line of code: 

```c++
std::cout << "Hello World!" << std::endl;
```

As the program is running, our computer will execute the lines of code that we type in order line by line. 

> Now, there are certain things that can break or change the order of execution of our code, and particyllarly they're refered to as control flow statements or calls to other functions, but in general the idea is that our code get's executed line by line.

<hr>

Now, one little note here to those who are familiar with functions. 

We can see that our main function returns an `int` but we don't return anything in the end of our code. 
Why is that? 
Well that's a special case **ONLY** for the main() function. 
`If you don't return anything inside main() it will assume that we are returning the number 0`

<hr>

Now let's get a bit to the syntax. 

What is actually the `<<` symbol? 

Well, it is called an overloaded operator and the best way to thing of it is... to think of it as a **function**.

Well obviously it looks like an operator and not a function, **BUT**. 

> Operators are just functions! 

So for example you can think of the following statement: 

```c++
std::cout << "Hello World!" << std::endl;
```

written as: 

```c++
std::cout.print("Hello World!").print(std::endl);
```

That's all it is. Think of operators as functions. 

So, what we do in the above statement is simply, push the string "Hello World!" into the cout function so it can get printed to the console, and then we're pushing an endline (`endl`). This one just tells to our console to print an ("enter") to the screen which is basically a new line.

And finally the 

```c++
std::cin.get();
```

simply means, pause at this line until we press enter on our keyboard to move onto the next line of code. 

It seems that there is no use of this line of code here at all, but it is often used when you write code to a program called Microsoft Visual Studio and you want to see your output to the console, but because the console closes unexpectadly fast, you just make it hang up by using the above line of code. And it will basically close when you press enter. 

So, now that we explained what our source file does, we still have to explain how do we get to the executable file so we can see the "Hello World" text on our console. 

So, first of all as we said previously the first thing that is going to happen is the "execution" of our preproccessor statements. In our example the `#include <iostream>` one. So once that is done, then the next step is the compilation of our code and the translation from the compiler, of our file into machine code. There are several important settings that determine how this actually happens. 
We will talk about that later on when we're going to analyze how the C++ compiler works. 

Now, each cpp file in our project get's compiled. Header files to not get compiled. 

What are header files? 

The ones that we include in our cpp files. Reminds of something? 

Oh yeah, the `#include <iostream>` so the iostream is called a header file. 

But remember, we do include that file into our cpp file, and we said that we literally copy paste that file by the #include preproccessor statement into our cpp file, so doesn't that mean that at this time the header file will be compiled? Kinda yes! But it's not the header file itself that is being compiled, it's the cpp file that now contains the contents of the header file that we included.

Now, every cpp file get's compiled individually and it's compiled into something called an `object` file aka `.obj`. 

Now, from each compiled `.cpp` file we get a `.obj` file and we need somehow to stitch them all together into a final executable file so that we can run and see the results of our program. 

The one who is responsible for doing what we exactly mentioned in the above statement is the `Linker`. 

We will analyze how the linker works in detail later on. 

If we could say very simply in one sentence though what it does is: `it glues all the .obj files together`.

## ⚙️ How the C++ compiler works!

So, where do we start with? 
Remember that basically all it is where we start from is a cpp file where we just write a bunch of text. Like the ones you're reading right now. Literally a bunch of characters written in a specific order. Now, to go from that first form (the file that contains simply text) to an actual executable binary, we basically need 2 main operations to happen. 

1. Compiling
2. Linking

So let's first cover the 1st one. 

Compiling. 

> The only thing the actual C++ compiler needs to do is, to take our text file and convert them into an intermediate format called an object file. 

And then all of those object files can be passed on to the linker so he can perform the linking, aka, the gluing of all those files as we previously discussed. 

Moving on, the compiler does several things when it produces these object files. 

Firstly, it needs to preprocess our code. That means that each preprocessor statement get's evaluated on that point.

Once our code is preprocessed we mote into tokenizing and parsing and basically what those mean is sorting out those "English" C++ text that we wrote into a format that the compiler can actually understand and reason with. This is something resulted into something called `Abstract Syntax Tribbing` to be created. Which is basically a representation of our code, but as an abstract syntax tree. 

The compiler's job at the end of the day is to create all our code into either constant data or instructions. 

Once the compiler has created this abstract syntax tree it can begin actually generating code. This code will be the actual machine code that the CPU is going to execute. We also end up with varius other data. Such as a place to store all of our constant variables. 

And that is essentially all what the compiler does. 

> At this point let's try to do something pretty cool! 

### ❗❣️ Crazy stuff going on here 

Remember when we previously said that the preprocessor statement `#include` all that does is take the file that is specified after it and literally copy paste it's content into our cpp file? Well let's prove that. 

Let's say we have the following C++ code, 

File: `addNumbers.cpp`

```c++
int addNumber(int x, int y) 
{
    return x + y;
}
```

Simply we wrote a function that takes as input 2 integer and returns their sum. 

If we try to compile the above code, it should compile successfully without any errors. 

Now let's say that we forget the closing brace at the end of our code, so it looks like this: 

```c++
int addNumber(int x, int y) 
{
    return x + y;
                        /// <--- notice the closing curly brace missing here
```

If we compile the below code we should get an error that we do miss a closing curly brace on line 4. 

How can we fix that? 

Either we can simply edit the file and add back our closing curly brace, or we can get a bit crazy and prove our very first statement of `#include` preprocessor statement literally copy pasting into our `addNumbers.cpp` file the content of the header file that is after our include statement. 

So let's create a header file. 

File: `closingBrace.h`

```cpp
}
```

Yeah, exactly, our closingBrace.h file simply contains one character. The closing curly brace itself --> `}`

Now take a look at the below code, 

```c++
int addNumber(int x, int y) 
{
    return x + y;
#include "closingBrace.h"
```

What do you think will happen if we compile this file? 

Well, it will compile properly without any errors. 

Why is that? 

Well, if you create the 2 files above in Microsoft Visual Studio and compile them, you can then see in your project a file with the extension `.i` in particular you will see a file called: `closingBrace.i` 

What this file is, is simply a file that is generated by the Microsoft Visual Studio compiler and it simply contains the contantes of the output of the preprocessor. 

Well if you go on and open that file you will see the following contents: 

```c++
int addNumber(int x, int y) 
{
    return x + y;
}
```

Does it remind you of anything? 

Well that was the proof that the preprocessor translated our `#include "closingBrace.h"` statement into a simple `}` character. And that is because it literally copy pasted the contents of the closingBrance.h file and replaced our #include statement with that content, and since we simply had only a `}` inside that file, that's what it copy pasted on that particular line that we placed our statement. 

And that's all there is to it about the `#include` preprocessor statement and also about how we do use header files aka `.h` files in C++! 

<hr>

You can have a look at [this](https://www.youtube.com/watch?v=3tIqpEmWMLI&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=6) particular excellent video, from where I got most of the things I wrote here about how the C++ compiler works! Congratulations to the amazingly knowledgable video creator. 

<hr>