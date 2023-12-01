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

# 10. What is Call Stack?

Call Stack keeps track of where we are in the code so that the program runs in order.

In the call stack, items are stored in a 'first-in, last-out' manner, following the principle of Last In, First Out (LIFO). As functions are executed, they are added to the top of the call stack, and when a function completes its execution, it is removed from the stack.

# 11. What is Stack Overflow?

When you keep calling functions that are nested inside each other.

![MemoryHeap](https://github.com/MunnazzahAslam/javascript-advanced-concepts/blob/main/stack%20overflow.png)

# 12. What is a Garbage Collector?

JavaScript is a garbage collected language. If you allocate memory inside of a function, JavaScript will automatically remove it from the memory heap when the function is done being called. However, that does not mean you can forget about memory leaks. No system is perfect, so it is important to always remember memory management.

JavaScript completes garbage collection with a mark and sweep method.

var person = {
 first: "Brittney",
 last: "Postma"
};
person = "Brittney Postma";

In the example above a memory leak is created. By changing the variable person from an object to a string, it leaves the values of first and last in the memory heap and does
not remove it. This can be avoided by trying to keep variables out of the global namespace, only instantiate variables inside of functions when possible. 

JavaScript is a single threaded language, meaning only one thing can be executed at a time. It only has one call stack and therefore it is a synchronous language.

# 13. Whats the issue with being synchronous?

So, what is the issue with being a single threaded language? Lets's start from the beginning. When you visit a web page, you run a browser to do so (Chrome, Firefox,
Safari, Edge). Each browser has its own version of JavaScript Runtime with a set of Web API's, methods that developers can access from the window object. 

In a synchronous language, only one thing can be done at a time. Imagine an alert on the page, blocking the user from accessing any part of the page until the OK button is clicked. If everything
in JavaScript that took a significant amount of time, blocked the browser, then we would have a pretty bad user experience. This is where concurrency and the event loop come in.

# 14. Explain Event Loop and Callback Queue?

When you run some JavaScript code in a browser, the engine starts to parse the code. Each line is executed and popped on and off the call stack. But, what about Web API's?
Web API's are not something JavaScript recognizes, so the parser knows to pass it off to the browser for it to handle. When the browser has finished running its method, it puts
what is needed to be ran by JavaScript into the callback queue. The callback queue cannot be ran until the call stack is completely empty. So, the event loop is constantly
checking the call stack to see if it is empty so that it can add anything in the callback queue back into the call stack. And finally, once it is back in the call stack, it is ran and then popped off the stack.

![MemoryHeap](https://github.com/MunnazzahAslam/javascript-advanced-concepts/blob/main/js-v8.png)



