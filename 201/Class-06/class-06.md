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

<h1>Introduction to the DOM</h1>

The Document Object Model (DOM) is the data representation of the objects that comprise the structure and content of a document on the web.

**What is the DOM?**
The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. The DOM represents the document as nodes and objects; that way, programming languages can interact with the page.

A web page is a document that can be either displayed in the browser window or as the HTML source. In both cases, it is the same document but the Document Object Model (DOM) representation allows it to be manipulated. As an object-oriented representation of the web page, it can be modified with a scripting language such as JavaScript.

For example, the DOM specifies that the querySelectorAll method in this code snippet must return a list of all the <p> elements in the document:

const paragraphs = document.querySelectorAll("p");
// paragraphs[0] is the first <p> element
// paragraphs[1] is the second <p> element, etc.
alert(paragraphs[0].nodeName);

All of the properties, methods, and events available for manipulating and creating web pages are organized into objects. For example, the document object that represents the document itself, any table objects that implement the HTMLTableElement DOM interface for accessing HTML tables, and so forth, are all objects.

The DOM is built using multiple APIs that work together. The core DOM defines the entities describing any document and the objects within it. This is expanded upon as needed by other APIs that add new features and capabilities to the DOM.

**DOM and JavaScript**
The previous short example, like nearly all examples, is JavaScript. That is to say, it is written in JavaScript, but uses the DOM to access the document and its elements. The DOM is not a programming language, but without it, the JavaScript language wouldn't have any model or notion of web pages, HTML documents, SVG documents, and their component parts. The document as a whole, the head, tables within the document, table headers, text within the table cells, and all other elements in a document are parts of the document object model for that document. They can all be accessed and manipulated using the DOM and a scripting language like JavaScript.

The DOM is not part of the JavaScript language, but is instead a Web API used to build websites. JavaScript can also be used in other contexts. For example, Node.js runs JavaScript programs on a computer, but provides a different set of APIs, and the DOM API is not a core part of the Node.js runtime.

The DOM was designed to be independent of any particular programming language, making the structural representation of the document available from a single, consistent API. Even if most web developers will only use the DOM through JavaScript, implementations of the DOM can be built for any language.

**Accessing the DOM**
You don't have to do anything special to begin using the DOM. You use the API directly in JavaScript from within what is called a script, a program run by a browser.

When you create a script, whether inline in a <script> element or included in the web page, you can immediately begin using the API for the document or window objects to manipulate the document itself, or any of the various elements in the web page (the descendant elements of the document). Your DOM programming may be something as simple as the following example, which displays a message on the console by using the console.log() function:

<body onload="console.log('Welcome to my home page!');">
  …
</body>

As it is generally not recommended to mix the structure of the page (written in HTML) and manipulation of the DOM (written in JavaScript), the JavaScript parts will be grouped together here, and separated from the HTML.

**Fundamental data types**
This page tries to describe the various objects and types in simple terms. But there are a number of different data types being passed around the API that you should be aware of.

**NOTE**: Because the vast majority of code that uses the DOM revolves around manipulating HTML documents, it's common to refer to the nodes in the DOM as elements, although strictly speaking not every node is an element.

There are also some common terminology considerations to keep in mind. It's common to refer to any Attr node as an attribute, for example, and to refer to an array of DOM nodes as a nodeList. You'll find these terms and others to be introduced and used throughout the documentation.

**DOM interfaces**
This guide is about the objects and the actual things you can use to manipulate the DOM hierarchy. There are many points where understanding how these work can be confusing. For example, the object representing the HTML form element gets its name property from the HTMLFormElement interface but its className property from the HTMLElement interface. In both cases, the property you want is in that form object.

But the relationship between objects and the interfaces that they implement in the DOM can be confusing, and so this section attempts to say a little something about the actual interfaces in the DOM specification and how they are made available.

**Interfaces and objects**
Many objects implement several different interfaces. The table object, for example, implements a specialized HTMLTableElement interface, which includes such methods as createCaption and insertRow. But since it's also an HTML element, table implements the Element interface described in the DOM Element Reference chapter. And finally, since an HTML element is also, as far as the DOM is concerned, a node in the tree of nodes that make up the object model for an HTML or XML page, the table object also implements the more basic Node interface, from which Element derives.

When you get a reference to a table object, as in the following example, you routinely use all three of these interfaces interchangeably on the object, perhaps without knowing it.

**Adding a child element**
This example uses a <div> element containing a <div> and two <button> elements. When the user clicks the first button we create a new element and add it as a child of the <div>. When the user clicks the second button we remove the child element. We use:

Document.querySelector() to access the <div> and the buttons
EventTarget.addEventListener() to listen for button clicks
Document.createElement to create the element
Node.appendChild() to add the child
Node.removeChild() to remove the child.