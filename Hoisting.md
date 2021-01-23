# 🔥🕺🏼 JavaScript Visualized: Hoisting

Hoisting is one of those terms that every JS developer has heard of because you googled your annoying error and ended up on StackOverflow, where this person told you that this error was caused because of **HOISTING** 🙃 So, what does it mean? (BTW - scopes will be covered in the next post, its better to keep docs small and focused).

If you're new t JS, you may have experienced "weired" behavior where some variables are randomly `Undefined`, `ReferenceError`s get thrown. Hoisting is often explained as putting varaibles and functions to the top of the file but NOOOOO, that not what's happening, although the behavior might seems little bit like this 😄.

When the JS engine get the script, the first thing it does it **Setting up memory** for the data in the code (Btw you can use the developer tools inside of sources you will find all the threads and scopes inside of your code, also you can watch the call )