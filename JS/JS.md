# JavaScript (Questions)

### Links

[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
[Stages of the TC39 Process](https://nitayneeman.com/posts/introducing-all-stages-of-the-tc39-process-in-ecmascript/)

### Questions

<details>
  <summary>What are Truthy and False values?</summary>

What are Truthy and False values?

Falsy values:

false, 0, “”, undefined, NaN

Truthy values:

Truthy values are everything except falsy values.

</details>

<details>
  <summary>What is the difference between Null and Undefined?</summary>

Undefined can be found in different ways. Such as for not setting value, accessing elements or proper which do not exist.

For null a value, we will have to set it.

</details>

<details>
  <summary>What are the difference between double equal (==) and triple equal (===)?</summary>

Triple(===) check the value and type both.

Double(==) convert type and after that compare values. At the time of converting and, comparing it follows its own rules.

</details>

<details>
  <summary>What is the closure?</summary>

When we call or return a function inside of another method, they create a closed environment.

</details>

<details>
  <summary>What is the difference between Bind, Call and Apply?</summary>

If we have any method inside an object and we want to apply that to another one, in that case, we can use the Bind, Call and Apply method.

Firstly, Call: Need to call the Call method and send the object and parameters with separating a coma.

Secondly, Apply: It is possible to call the Applymethod and send the object and other parameters through an array.

Third, Bind: If it is needed to use a method, again and again, need to bind it with the new object. The bind creates a new function that will call the original one with context.

It is not possible to use Bind, Call and Apply with the arrow function.

</details>

<details>
  <summary>What is the Window?</summary>

A window is a global object that provides an interface for working with a DOM model of a document. It is possible to use the window object in each browser.

</details>

<details>
  <summary>What is a global variable?</summary>

A global variable is a variable that is available from any function.

</details>

<details>
  <summary>What is a setTimeout method?</summary>

The setTimeout method evaluates an expression or calls a function after a specified time.

</details>

<details>
  <summary>What is a setInterval method?</summary>

The setInterval method will continue calling the function until the interval would be active.

</details>

<details>
  <summary>What data types are in JavaScript?</summary>

The JavaScript language has two groups of data types: primitive data types and referential data types. The difference between the groups in access type. Primitive gets by value. Referential gets by link.
The data types: Number, BigInt, String, Boolean, null, undefined, Object, Symbol.

</details>

<details>
  <summary>How to check that the object is an array?</summary>

It is possible to check that object is an array by Array.isArray method or duck typing.

</details>

<details>
  <summary>How to check if a number is finite?</summary>

But they have a difference in behaviour. The global isFinite try to turn the string value into a number.

</details>

<details>
  <summary>How to check that a variable is NaN?</summary>

* isNaN - return true for NaN and undefined.
* Number.isNaN - return true only for NaN.
* NaN only one variable that is not equal itself.

</details>

<details>
  <summary>What is the difference between var, let and const?</summary>

* var has a function visibility area and pops up
* let, const has a block visibility area and not pop up
* const cannot be reset

</details>

<details>
  <summary>What is the difference between callbacks, promises, async / await?</summary>

All of them are ways for working with async functionality.

* Callback allows putting function that will run with the result of the async operation.
* Promises is a modern way of working with async functionality. A promise is an object that contains its state and is a microtask.
* Async / Await is syntax sugar that provides a more comfortable way to work with promises.

</details>

<details>
  <summary>Is it possible to add new methods into standard classes?</summary>

It is possible, but it is not good practice. 

</details>

<details>
  <summary>What is the Promise in JavaScript?</summary>

A promise is an object that stores its state (pending, fulfilled, rejected). It is a more high-tech functionality for working with async code in JavaScript.

</details>

<details>
  <summary>What states does the Promise have?</summary>

* pending: initial state, neither fulfilled nor rejected.
* fulfilled: meaning that the operation was successful.
* rejected: meaning that the operation failed.

</details>

<details>
  <summary>What are methods from the Promise class?</summary>

* .resolve - cover value into success promise.
* .reject - cover value into error handler.
* .all - wait for all success promises or reject them if one has an error.
* .allSettled - returns all resolved and rejected Promises.
* .race - returns first success of failure promise.
* .any - returns any successful promise.

</details>

<details>
  <summary>What are the methods from the Promise prototype?</summary>

* then - set success and error handler.
* .catch - set error handler.
* .finaly - set a handler that is not dependent on the result (error or success).

</details>

<details>
  <summary>Explain TC39 Process?</summary>

This process is built from five stages, starting with stage zero. Any proposal for a change in the specification goes through these stages.
* Stage 0 (Strawperson):
It represents an initial idea for adding or changing the specification.
* Stage 1 (Proposal):
It describes a discrete problem or general need, suggests a shape of the solution and points out potential challenges.
* Stage 2 (Draft):
It describes the syntax, semantics and APIs, although it can have 'todo' comments or placeholders. An experimental implementation should be runnable by a browser or a build-time transpiler.
* Stage 3 (Candidate):
It is ready for feedback and refinements from implementations and users.
* Stage 4 (Finished):
It indicates that the proposal is ready to be included in the latest draft of the specification - and be delivered with its next edition.

</details>
