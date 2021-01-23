# 🔥🕺🏼 JavaScript Visualized: Hoisting

Hoisting is one of those terms that every JS developer has heard of because you googled your annoying error and ended up on StackOverflow, where this person told you that this error was caused because of **HOISTING** 🙃 So, what does it mean? (BTW - scopes will be covered in the next post, its better to keep docs small and focused).

If you're new t JS, you may have experienced "weired" behavior where some variables are randomly `Undefined`, `ReferenceError`s get thrown. Hoisting is often explained as putting varaibles and functions to the top of the file but NOOOOO, that not what's happening, although the behavior might seems little bit like this 😄.

When the JS engine get the script, the first thing it does it **Setting up memory** for the data in the code (Btw you can use the developer tools inside of sources you will find all the threads and scopes inside of your code, also you can watch the callStack).
No code is executed at this point, it's simply just preparing everything for execution. The way that function declarations and varaibles are stored is different. Functions are stored with a **reference of the entire function** 😅.
To give a clear explanation about this:

```javascript
      function x() {
        console.log('cRYP70N');
      }
```

In the global object inside of our developement tools we gonna find the function x located inside of the global Object like this

```Javascript
      function x() {
        console.log('cRYP70N');
      }
```

![Functions Hoisting](./Images/gif7.gif)

With variables, it’s a bit different. ES6 introduced two new keywords to declare variables: `let` and `const`. Variables declared with the `let` or `const` keyword are stored uninitialized.

![Variables Hoisting](./Images/gif8.gif)

Variables declared with the `var` keyword are stored with the default value of _`undefined`_.

![Variables var Hoisting](Images/gif9.gif)

Now that the creation phase is done, we can actually execute the code. Let's see what happens if we had 3 console.log statements on top of the file, before we declared the function or any of the variables.

Since functions are stored with a reference to the entire function code, we can invoke them even before the line on which we created them! 🔥

![Execution Phase](./Images/gif16.gif)

When we reference a variable declared with the `var` keyword before their declaration, it’ll simply return its default value that it was stored with: _`undefined`_! However, this could sometimes lead to "unexpected" behavior. In most cases this means you’re referencing it unintentionally (you probably don’t want it to actually have the value of `undefined`) 😬💁‍♂️

![Undefined where comes from](./Images/gif17.gif)

In order to prevent being able to accidentally reference an `undefined` variable, like we could with the `var` keyword, a `ReferenceError` gets thrown whenever we try to access uninitialized variables. The "zone" before their actual declaration, is called **_the temporal dead zone_**: you cannot reference the variables (this includes ES6 classes as well!) before their initialization.

![Temporal Dead Zone](./Images/gif18.gif)

When the engine passes the line on which we actually declared the variables, the values in memory are overwritten with the values we actually declared them with.

![Memory explanation](Images/gif19.gif)

All done! 🎉 Quick recap:

* Functions and variables are stored in memory for an execution context before we execute our code. This is called _hoisting_.
* Functions are stored with a reference to the entire functions, variables with the `var` keyword with the value of `undefined`, and variables with the `let` and `const` keyword are stored _uninitialized_.

I hope that the term hoisting is a bit less vague now that we've looked at what's happening when we execute our code. As always, don't worry if it still doesn't make a lot of sense yet. You'll get a lot more comfortable with it the more you work with it. Feel free to ask me for help, I'd love to help you! 😃
