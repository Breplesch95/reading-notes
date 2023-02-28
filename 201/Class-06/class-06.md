<h1>Problem Domain, Objects, and the DOM</h1>

Object basics
An object is a collection of related data and/or functionality. These usually consist of several variables and functions (which are called properties and methods when they are inside objects). Let's work through an example to understand what they look like.

To begin with, make a local copy of our oojs.html file. This contains very little — a <script> element for us to write our source code into. We'll use this as a basis for exploring basic object syntax. While working with this example you should have your developer tools JavaScript console open and ready to type in some commands.

As with many things in JavaScript, creating an object often begins with defining and initializing a variable.

The value of an object member can be pretty much anything — in our person object we've got a number, an array, and two functions. The first two items are data items, and are referred to as the object's properties. The last two items are functions that allow the object to do something with that data, and are referred to as the object's methods.

When the object's members are functions there's a simpler syntax. Instead of bio: function () we can write bio().

n object like this is referred to as an object literal — we've literally written out the object contents as we've come to create it. This is different compared to objects instantiated from classes, which we'll look at later on.

It is very common to create an object using an object literal when you want to transfer a series of structured, related data items in some manner, for example sending a request to the server to be put into a database. Sending a single object is much more efficient than sending several items individually, and it is easier to work with than an array, when you want to identify individual items by name.

**Dot notation**
Above, you accessed the object's properties and methods using dot notation. The object name (person) acts as the namespace — it must be entered first to access anything inside the object. Next you write a dot, then the item you want to access — this can be the name of a simple property, an item of an array property, or a call to one of the object's methods.

**Objects as object properties**
An object property can itself be an object.

person.age;
person.bio();

Objects as object properties
An object property can itself be an object. For example, try changing the name member from

const person = {
  name: ["Bob", "Smith"],
};

to

const person = {
  name: {
    first: "Bob",
    last: "Smith",
  },
  // …
};

To access these items you just need to chain the extra step onto the end with another dot. Try these in the JS console:

person.name.first;
person.name.last;

If you do this, you'll also need to go through your method code and change any instances of

name[0];
name[1];

to

name.first;
name.last;

Otherwise, your methods will no longer work.

Bracket notation
Bracket notation provides an alternative way to access object properties. Instead of using dot notation like this:

person.age;
person.name.first;

You can instead use brackets:

person["age"];
person["name"]["first"];

This looks very similar to how you access the items in an array, and it is basically the same thing — instead of using an index number to select an item, you are using the name associated with each member's value. It is no wonder that objects are sometimes called associative arrays — they map strings to values in the same way that arrays map numbers to values.

Dot notation is generally preferred over bracket notation because it is more succinct and easier to read. However there are some cases where you have to use brackets. For example, if an object property name is held in a variable, then you can't use dot notation to access the value, but you can access the value using bracket notation.

Setting object members
So far we've only looked at retrieving (or getting) object members — you can also set (update) the value of object members by declaring the member you want to set (using dot or bracket notation), like this:

person.age = 45;
person["name"]["last"] = "Cratchit";

Try entering the above lines, and then getting the members again to see how they've changed, like so:

person.age;
person["name"]["last"];

Setting members doesn't just stop at updating the values of existing properties and methods; you can also create completely new members. Try these in the JS console:

person["eyes"] = "hazel";
person.farewell = function () {
  console.log("Bye everybody!");
};

You can now test out your new members:

person["eyes"];
person.farewell();

One useful aspect of bracket notation is that it can be used to set not only member values dynamically, but member names too. Let's say we wanted users to be able to store custom value types in their people data, by typing the member name and value into two text inputs. We could get those values like this:

const myDataName = nameInput.value;
const myDataValue = nameValue.value;

We could then add this new member name and value to the person object like this:

person[myDataName] = myDataValue;

To test this, try adding the following lines into your code, just below the closing curly brace of the person object:

const myDataName = "height";
const myDataValue = "1.75m";
person[myDataName] = myDataValue;

Now try saving and refreshing, and entering the following into your text input:

person.height;

Adding a property to an object using the method above isn't possible with dot notation, which can only accept a literal member name, not a variable value pointing to a name.

**What is "this"?**

You are probably wondering what "this" is. The this keyword refers to the current object the code is being written inside — so in this case this is equivalent to person. So why not just write person instead?

Well, when you only have to create a single object literal, it's not so useful. But if you create more than one, this enables you to use the same method definition for every object you create.

In this case, person1.introduceSelf() outputs "Hi! I'm Chris."; person2.introduceSelf() on the other hand outputs "Hi! I'm Deepti.", even though the method's code is exactly the same in each case. This isn't hugely useful when you are writing out object literals by hand, but it will be essential when we start using constructors to create more than one object from a single object definition.

**Introducing constructors**
Using object literals is fine when you only need to create one object, but if you have to create more than one, as in the previous section, they're seriously inadequate. We have to write out the same code for every object we create, and if we want to change some properties of the object - like adding a height property - then we have to remember to update every object.

We would like a way to define the "shape" of an object — the set of methods and the properties it can have — and then create as many objects as we like, just updating the values for the properties that are different.

The first version of this is just a function:

function createPerson(name) {
  const obj = {};
  obj.name = name;
  obj.introduceSelf = function () {
    console.log(`Hi! I'm ${this.name}.`);
  };
  return obj;
}

This function creates and returns a new object each time we call it. The object will have two members:

a property name
a method introduceSelf().
Note that createPerson() takes a parameter name to set the value of the name property, but the value of the introduceSelf() method will be the same for all objects created using this function. This is a very common pattern for creating objects.

Now we can create as many objects as we like, reusing the definition:

const salva = createPerson("Salva");
salva.name;
salva.introduceSelf();

const frankie = createPerson("Frankie");
frankie.name;
frankie.introduceSelf();

This works fine but is a bit long-winded: we have to create an empty object, initialize it, and return it. A better way is to use a constructor. A constructor is just a function called using the new keyword. When you call a constructor, it will:

create a new object
bind this to the new object, so you can refer to this in your constructor code
run the code in the constructor
return the new object.
Constructors, by convention, start with a capital letter and are named for the type of object they create. So we could rewrite our example like this:

function Person(name) {
  this.name = name;
  this.introduceSelf = function () {
    console.log(`Hi! I'm ${this.name}.`);
  };
}

To call Person() as a constructor, we use new:

const salva = new Person("Salva");
salva.name;
salva.introduceSelf();

const frankie = new Person("Frankie");
frankie.name;
frankie.introduceSelf();

