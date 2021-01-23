TODO: -> Add a pic for it

# 🎉👨‍👩‍👧‍👧 JavaScript Visualized: Prototypal Inheritance

Have you ever wondred why we can use built-in methods such as `.length`, `.split()` (BTW It's so confusing to do it from scratch 😂), `.join()` (this one is pretty EZ BTW 😅) on our strings, arrays, or objects? We never explicitly specified them, where do they come from? Now don't say "It's JAVASCRIPT lol no one knows, it's maginx 🌟🤯" it's actually bceause of something called **Prototypal Inheritance**. it's pretty awesome, and you use it more often than you realize!

We often have to create many objects of the same type. Say we have a website where people can browse dogs!

For every dog, we need object that represent that dog! 🐶 instead of writing a new object each time, I'Il use a constructor function (I know what ur thinkg, I might cover ES6 classes later on!) from which we can create dog *Instances* using the `new` keyword (this is not for explaining constructor functions though, so I won't talk too much about that).

Every Dog has a name, a breed, a color, and a function to bark!

```Javascript
  function Dog(name, breed, color) {
    this.name = name;
    this.breed = breed;
    this.color = color;
    this.bark = () => `Wooooooof !!!`;
  }
```

When we create the `Dog` Constructor function, it wasn't the only object we created. Automatically, we also created another object, called the prototype! By default, this object contains a constructor properly, which is simply a reference to the original constructor function, `Dog` in this case.

TODO: -> Explanation GIF Plz

---

The `prototype` properly on the Dog constructor function is non-enumberable, meaning that it doesn't show up when we try to access the objects properties. But it's still there!

Okay so.. Why do we have this property object? First, let's create some dogs that we want to show. To keep it simple, I'Il call them just Dog1 and Dog2.
`Dog1` is Jack, a cute black Bergy (If i spell it right LOL)! `Dog2` is Rocky!

```javascript
  const dog1 = new Dog(
    'Jack',
    'Bergy',
    'Black'
    );
  
  const dog2 = new Dog(
    'Rocky',
    'Jack Russel',
    'White'
  );
```

Let's log `dog1` to the console, and expand its proerties!

TODO: -> Add a photo for the console.log(dog1);

We see the properties we added, like `name`, `breed`, `color`, and `bark`. But woad what is that `__proto__` property! INTERESTING!!! it's non-enumerable, meaning that it usually doesn't show up when we try to get the properties on the object.
Let's see what going on behind the scenes! 😁

TODO: -> Insert an expand of the __PROTO__

WOOW it looks like exactly the `Dog.prototype` object! Well `__proto__` is a reference to the `Dog.prototype` object. This is what **Prototypal Inheritance** is all about: wach instance of the constrcutor has access to the prototype of the constructor! 🤯 MIND BLOWING xD

TODO: An image to explain it so well here please

So why the heck is this cool?? Sometimes we have properties that all instances share.
For example the `bark` function in this case: it's the exact same for every dog so why we need to create a new instance of it each time.
Because all the constructors have access to the prototype of the constructor we don't need to do it each time 🌝
Also this might be useful to make our code faster just add it to the `Object.prototype` and start using it each time u need it 🥳

TODO: Also here we need one please

Whenever we try to access a property on the instance, the engine fist searches locally to see if the property is defined on the object itself.
However, if it can't find the property we're trying to access, the engine **WALKS DOWN THE PROTOTYPE CHAIN** through the `__proto__` property! remember from the scope chain! Exactly the same.

TODO: Okay another one please

now this is just one step, but it can contain several steps! if you followe along, you may have notice that I didn't include one property When I expanded the `__proto__` object showing the `Dog.prototype`. it's also an Object itself, meaning that it's actually an instance of teh `Object` Conctructor! that means that `Dog.prototype` also contains a `__proto__` property which is a reference to `Object.prototype`!

TODO: Please expand the rest of the object in a GIf

Finally we have an answer to where all the built-in methods come from:
  *THEY ARE ON THE PROTOTYPE CHAIN* 😆

For example the `.toString()` method. Is it defined locally on the `dog1` object? HMMM No 🚫 is it defined on the object `dog1.__proto__` has a ref to, namely `Dog.prototype`? Also NOOOOP, Is it defined on the object `Dog.prototype.__proto__` has a ref to namely `Object.prototype`> YEEES 👏

TODO: The final prototypal inheritance photo

Now, we've just been using constructor functions (`function dog() {...} `), which is till valid JavaScript. However, ES6 actually introduced an easier syntax for constructor functions and working with prototypes: ***CLASSES***
