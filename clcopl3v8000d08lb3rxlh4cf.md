# A Beginner’s Guide to Understanding the Lifecycle of a JavaScript Promise

***Promises*** are a fundamental part of modern JavaScript development, but for beginners, they can be a confusing and intimidating concept. In this beginner's guide, we'll take a deep dive into the lifecycle of a JavaScript ***promise***, starting from its creation and progressing through its various states and eventual **resolution** or **rejection**.

By the end of this article, you'll have a solid understanding of how ***promises*** work and how to use them effectively in your own code. Whether you're a complete newcomer to JavaScript or an experienced developer looking to brush up on your skills, this guide has something for everyone. So, let's get started!

## **Prerequisite**

* Fundamental knowledge of  JavaScript (preferably Synchronous and Asynchronous)
    
* Fundamental knowledge of the working of a Browser’s Dev Tools.
    
* A code editor and browser.
    

## **Introduction**

In JavaScript, the term "***synchronous***" refers to the occurrence of events in a sequential, ordered manner. This means one event must be completed before the next event begins. An example of this is when you make a function call and wait for the return value. The code execution is blocked until the function returns a value, and then the next line of code is executed.

On the other hand, "***asynchronous***" refers to the occurrence of events independent of the main program execution. This means that multiple events can occur concurrently and the main program will not be halted while waiting for these events to finish. An example of this is when you make a request to a server. The program continues running while waiting for a response.

JavaScript is primarily a ***synchronous*** language, but it also has mechanisms for handling ***asynchronous*** events through the use of ***callback functions***, ***Promises***, and ***async/await***. These features allow JavaScript programs to perform tasks concurrently, rather than waiting for each task to complete in sequence.

## **What is a Promise?**

A JavaScript ***promise*** can be thought of as a "***guarantee***" made by a function to return a value at some point in the future. It can be seen as a placeholder for a value that is not yet known and allows the program to continue executing while the value is being ***resolved***.

Here's an example analogy: Imagine you and a friend are at a restaurant, and you ask the waiter for the daily special. The waiter ***promises*** to check with the chef and bring back the answer. While waiting, you can continue talking with your friend or ordering other items from the menu. When the waiter returns with the answer, he fulfills his ***promise*** by telling you about the daily special. In this analogy, the waiter is like a JavaScript ***promise***. The daily special is like the ***resolved*** value that the ***promise*** represents. The process of the waiter going to check with the chef and returning with an answer represents the ***asynchronous*** process of a ***promise*** being ***resolved***.

Keep in mind that a promise may produce a single value some time in the future which is either **resolved** or **rejected,** but more about that later 🌚.

## **Why use Promises?**

Promises are modern ES6 features that have become an integral part of the JavaScript language due to the following reasons.

* ***Promises*** provide a way to handle asynchronous operations in a more synchronous-like fashion, i.e they allow you to write code that looks like it is executing in a sequential manner, even though it’s asynchronous operations that take some time to complete.
    
* Using ***promises*** makes your code easier to read and maintain, allowing you to avoid "***callback hell***" - a situation where you have nested callback functions that can make your code difficult to understand and maintain.
    
* ***Promises*** also provide a standard way to handle errors that may occur during an asynchronous operation.
    
* Finally, ***promises*** allow you to chain asynchronous operations together in a more concise and readable manner.
    

## **The Lifecycle of a JavaScript Promise**

A ***promise*** is used to handle asynchronous operations, and as such, its state changes over time. There are several states that a promise can exist in, such as:

* **Pending State**: Once a promise is created, it enters the ***pending*** state. While a ***promise*** is in the pending state, the outcome of the asynchronous operation is still unknown. A ***promise*** remains ***pending*** until it is either ***resolved*** by the completed async operation or **rejected** due to failure of the async operation.
    
* **Fulfilled State**: This is the state of a ***promise*** which indicates that the asynchronous operation has been completed successfully and the ***promise*** has a ***resolved*** value.
    
* **Rejected State**: This is the state of a ***promise*** which indicates that the asynchronous operation has failed and the ***promise*** has a ***rejected*** value.
    
* **Settled State**: A ***promise’s settled*** state refers to the final state of the ***promise*** after it has been ***fulfilled*** or ***rejected***.
    

A pictorial representation of the lifecycle would be

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673191889554/b723ca34-f299-473e-9d21-9f6605cee053.png align="center")

Let's build our first ***promise*** to fully grasp the concept of a ***promise***.😉

## **Building a Promise**

We can build a ***promise*** using the ***Promise constructor*** and store that result in a variable.

```javascript
const promise = new Promise ();
```

This constructor takes in exactly one function (the ***executor function***) as an argument.

```javascript
const promise = new Promise (function() {
});
```

The ***executor function*** is responsible for performing the asynchronous operation. This function receives two arguments – ***resolve*** and ***reject***.

```javascript
const promise = new Promise(function (resolve, reject) {});
```

The ***resolve*** function is used to indicate that the asynchronous operation has been completed successfully, while the ***reject*** function is used to indicate that the operation has failed.

Logging our promise to the console so far, we have

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673192060947/3f8006e9-f199-47ad-ae1e-5be3f64055e8.png align="center")

As we can see, the moment we created our ***promise***, we began its lifecycle.

Next, let’s simulate a simple condition that triggers either the ***resolve*** or ***reject*** function. Our condition involves the following steps:

* Generate a random number between ***0*** and ***1***.
    
* ***Resolve*** the value of our ***promise*** if our random number is equal to or above ***0.5***
    
* ***Reject*** the value of our ***promise*** if our random number is below ***0.5***
    

First, we create our random number between 0 and 1.

```javascript
let randNum = Math.random();
```

Looking at our result in the console gives:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673215233623/e2b02891-6d32-47f1-a554-52d75bbd986a.gif align="center")

As you can see, every time we refresh the browser, our random variable generates a new value.

Next, we use an ***if...else*** block to pass in our conditions.

```javascript
if (randNum >= 0.5) {

} else {
 
}
```

Finally, we call the ***resolve*** and ***reject*** methods with corresponding messages depending on the value produced by our random variable.

```javascript
const promise = new Promise(function (resolve, reject) {
  let randNum = Math.random();
  console.log(randNum);
  if (randNum >= 0.5) {
    resolve("Promise Resolved");
  } else {
    reject("Promise Rejected");
  }
});
```

Taking a look at what we’ve achieved so far, we have:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673215263384/97a37a94-4577-4669-be71-8d53feb1af63.gif align="center")

As you can see, every time we refresh the page, our random number changes and our promise is either ***resolved*** or ***rejected.***

And with this, we’ve successfully built our first promise, bravo! 🥳

## **Consuming a Promise**

Consuming a ***promise*** means processing the result of a ***promise*** and taking action based on its outcome. When we consume a ***promise***, we simply take the value gotten from the ***promise (the resolved or rejected value)*** to process another operation.

### **Methods of Consuming a Promise**

A promise can be consumed using any of the following methods:

* The ***then*** method: The ***then*** method allows you to specify a function that should be called when a ***Promise*** is fulfilled (i.e., when the asynchronous operation represented by the ***Promise*** has been completed successfully). An example of the ***then*** method in use is
    
    ```javascript
    myPromise.then(result => {
    	//Whatever we want to do with the result
    });
    ```
    
* The ***catch*** method: The ***catch*** method is used to handle ***Promises*** that have been ***rejected***, or ***unsuccessful***. It allows us to specify what should happen when a ***promise*** is rejected so that we handle the error appropriately in our code. An example of the ***catch*** method in use is
    
    ```javascript
    myPromise.catch(result => { 
    //However we want to represent our error
    });
    ```
    
* The ***finally*** method: The ***finally*** method is used to specify a callback function that is executed when the ***promise*** is ***settled*** (i.e., either ***resolved*** or ***rejected***). It has the following syntax:
    
    ```javascript
    myPromise.finally(onFinally)
    ```
    
    In our above example, the “***onFinally”*** function is the function that is called when the ***promise*** is settled. Note that the callback function of a ***finally*** method is not passed any arguments when it is called.
    
* The ***async/await*** method: The ***async/await*** method is a way to write asynchronous code in a synchronous-looking style. It allows you to use the **async** operator to specify that a function is asynchronous and the ***await*** operator to wait for a ***promise*** to be ***resolved*** or ***rejected***, rather than using the ***then*** and ***catch*** methods. Keep in mind that this method uses a ***try…catch*** block ( a block of code used to **try** to run an async operation and **catch** any errors that may occur during execution).
    
    An example of the ***async/await*** method in use is:
    
    ```javascript
    const  myPromise = async function() { 
        try { 
         Const randNum = await Math.random()
      } catch(error) { 
        } 
    } 
    myPromise();
    ```
    
    Enough theoretical talk, let’s test these methods! 😁
    

### **Experimenting with the Promises Methods**

Let's utilize the ***promise*** we created earlier and try out some creative approaches using these methods.

Recall that our ***promise*** looks like this

```javascript
const promise = new Promise(function (resolve, reject) {
  let randNum = Math.random();
  console.log(randNum);
  if (randNum >= 0.5) {
    resolve("Promise Resolved");
  } else {
    reject("Promise Rejected");
  }
});
```

Let’s consume this ***promise*** using the ***then*** and ***catch*** methods

First, we consume our ***promise*** with the ***then*** method and log it to the console (the ***resolved*** value).

```javascript
promise.then((result) => console.log(result));
```

Then we catch any ***rejected*** result with the ***catch*** method and log it to the console.

```javascript
promise.catch((error) => console.error(error));
```

For a visual example, we can use the media below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673215316292/4ed47431-45e3-4e3c-aef5-05185e75fe4b.gif align="center")

As you can see, every time our random number yields a value greater than or equal to ***0.5***, the string “***Promise Resolved***” is logged to the console, and if the value is smaller than ***0.5***, the string “***Promise Rejected***” is logged to the console. And with that, we’ve successfully consumed our promise! Big props to you 🙌. Finally, let’s learn about combining promises (***promise chaining***).

## **Promise Chaining**

***Promise chaining*** is a technique in which the result of one ***promise*** is passed on to another ***promise***, enabling async operations to run in a specific order. In a ***promise*** chain, the value returned from a ***promise*** is passed to the next ***promise*** in the chain, allowing multiple ***promises*** to be executed in order rather than being nested or run in parallel.

To make an example of ***promise chaining***, let’s chain our previously built promise.

Recall that our promise looks like this

```javascript
const promise = new Promise(function (resolve, reject) {
  let randNum = Math.random();
  console.log(randNum);
  if (randNum >= 0.5) {
    resolve("Promise Resolved");
  } else {
    reject("Promise Rejected");
  }
});
```

First, we consume our promise with the ***then*** method

```javascript
promise.then((result) => console.log(result))
```

Then, we chain the next method (***catch***) to it. To do this, we simply attach the next method at the end of the first.

```javascript
promise
  .then((result) => console.log(result))
  .catch((error) => console.error(error))
```

Finally, we chain our last method (***finally***)

```javascript
promise
  .then((result) => console.log(result))
  .catch((error) => console.log(error))
  .finally((secResult) => console.log("It worked"));
```

Taking a look at our console for clarity

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673215340937/57adfff9-3a9e-4fce-8a4f-ebfca10e547f.gif align="center")

As you can see, we were able to catch both ***resolved*** and ***rejected*** values using ***promise chaining***. We also made use of the ***finally*** method which runs after the promise is settled.

## **Where to go from here?**

The next step would be to learn about the ***Fetch API***, how it works in JavaScript and how to use the ***Fetch API*** to request data from external sources. This way, you can use methods such as ***async/await*** together with the ***Fetch API*** to build dynamic functionalities in web applications and fetch data for users.

## **Project Link**

[**GitHub**](https://github.com/Daiveedjay/Promise-Article)

## **Conclusion**

In summary, it is essential for developers to understand the lifecycle of JavaScript ***promises*** in order to effectively use asynchronous programming in their code. ***Promises*** offer a straightforward and effective way to manage asynchronous tasks, and by comprehending how they are created, fulfilled and rejected, developers can write organized and efficient code. To summarize, the journey of a JavaScript promise begins as an idea and ends with either fulfillment or rejection. Despite the outcome, working with promises is always an exciting experience. As a reminder, anything can happen when working with promises, so have fun with it! 😉