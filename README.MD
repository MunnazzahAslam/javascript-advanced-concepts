# 1. What is a Javascript engine?

A JavaScript engine is *a computer program that you give JavaScript code to and it tells the computer how to execute it*. 

It is a translator for the computer between JavaScript and a language that the computer understands. 

But what happens inside of the engine? Well, that depends on the engine. There are many JavaScript Engines out there and typically they are created by web browser vendors. All engines are standardized by ECMA Script or ES.

# 2. What is Parsing?

Parsing is the process of analyzing the source code, checking it for errors, and breaking it into parts.

# 3. What is AST?

Abstract Syntax Tree is a type of data structure produced by the process of parsing.

AST is a type of tree graph of the code structure. Certain things are implicit in the structure hence the name abstract.

# 4. What is an Interpreter?

An interpreter directly executes each line of code one by one, without needing them to be compiled into a machine language program.

# 5. What is a compiler? 

The compiler works ahead of time. It takes JavaScript code and converts it into a language that is easier for the browser to understand.

Babel is a compiler that converts modern JS code into old JS code.
Typescript is a superset of JavaScript that compiles down to JavaScript.

# 6. How do all these things work in modern engines?

In modern engines, the interpreter starts by reading the code line by line, and the profiler watches frequently used codes and flags then passes it to the compiler to optimize it.

In the end, the JavaScript engine gets the bytecode produced by the interpreter and mixes in the optimized compiled code and this is called Just in Time compilation.

# 7. What is Memoization?

Memoization is a way to cache the return value from a function based on its parameter to increase performance after one execution.

function memoizedAppendToString() {
    let cache = {};
    return function (user) {
    if (user in cache) {
        console.log(cache[user]);
    } else {
    console.log('Long time');
    cache[user] = user;
    console.log(cache[user]);
    }        
    }
}

const memoizedAppend = memoizedAppendToString();
memoizedAppend('madiha');
memoizedAppend('madiha');
memoizedAppend('madiha');
memoizedAppend('moiz');

Output:
Long time
madiha
madiha
madiha
Long time
moiz

# 8. What are hidden classes in JavaScript?

https://richardartoul.github.io/jekyll/update/2015/04/26/hidden-classes.html

# 9. What is a Memory Heap?

Memory Heap is a place to allocate, use, and remove memory as required. It is used to store information so that we can use our memory appropriately.

![MemoryHeap](https://github.com/MunnazzahAslam/javascript-advanced-concepts/blob/main/memory-heap.png)







