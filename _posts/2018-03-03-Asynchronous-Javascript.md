# Synchronous vs Asynchronous

Let's start with an example. 
Suppose you went out with a date with to a restaurant, one of those places where they serve the order in fornt of the counter, right after placing the order. (Looking at you, Subway).

Now unless you complete placing and getting back the order, there's no way you can come back to your date, who's sitting alone in the table. Or, in other words, obtaining the food is **synchronous (or blocking)**, as it blocks the flow of the date. 

Now let's consider the case, in which the restaurant gives you some kind of receipt/token. So initially you would stand in the queue and get back a token, then come back to your table. Only when you order no. is displayed, you will have to go and collect your order. Here, the two actions aren't *blocking*, rather they are happening **asynchronously.**

You've probably heard how writing asynchronous code in Javascript is extremely important. But before getting into *how* to write async code, let's figure out *why* asynchronous operations are required.

# But why async?

When Javascript is executed, synchronous code has the potential to block execution until it has finished the operation it is performing. Often, this spawns some terrible results if the process is really intensive or buggy. This is one of the reasons why sometimes your chrome tab will become unresponsive.

Hence a lot of events happening in the browser or in the server in case of Node.js (file handling, http requests) has to happen asynchronously. For example, when new comments appear on your Facebook post, they don't block any other functions of the site. Hence, it happens *asynchronously*.

# Handling Async functions: Callbacks

One approach to asynchronous programming is to provide a *callback* to functions which perform time-consuming actions. Callbacks are ultimately functions themselves which are called at the end of the slow action. This is possible because in Javascript, functions are first class objects. Here is an example of a callback function

```
// assuming getUser is an async function to get an user from database
console.log('Getting User');
const user = User.getUser(id, (err,users)=&amp;amp;gt;{
    if(err){
        console.log('Error in getting User!');
        return;
    }
    console.log('Got User!');
}
console.log('Finished Getting User.');
```

This will output the following: 

```
Getting User
Finished Getting User
Got User!
```

Here, the third console.log statement actually got printed before the second one, because the function getUser is an asynchronous, and it doesn't block the code which follows it. As it takes some time to obtain the users from the database, hence the third statement is executed early.

#### Few Quirks about Callbacks

- Callbacks don't necessitate functions to be asynchronous. A function can call a callback in both synchronous and asynchronous way. Here's the fucntion getUser which actually gets the users fron database, which invokes the callback in both synchronous and asynchronous way.

```
function getUser(id, callback){
    if(typeof id !== string){
        return callback(new TypeError(&amp;amp;quot;Must be string&amp;amp;quot;);) //sync operation
    }
    User.find({_id: id}, (user)=&amp;amp;gt;{
        return callback(null, user); //async operation
    });
}
```
- Callbacks, although can be nested, often results in unreadable and hard-to-maintain code, often referred to as [Callback Hell](http://callbackhell.com/).

# Handling Async functions: Promises

Working with abstract concepts is easier and often more intuitive. For asynchronous acions, we could, instead of specifying the functions to be called at some point in the future, return an object which is a representation of *the future event* itself.

That is exactly when Promise Class comes in. Promise is an asynchronous action that may complete at some point and produce a value. Let's go back to the restuarant date for a moment.

```
// order function which returns promise
function orderPizza (type) {
  return new Promise( (resolve, reject) =&amp;amp;gt; {
    var pizza = cookPizza(type);
    pizza.ready = function (err, pizza) {
      if (err) {
        return reject(Error('Duh! Dough shortage!'));
      }
      return resolve(pizza);
    }
  })
}
```

Remember the token given by the counter specifying the order number? That's a promise of the restaurant that your order will get processed. Now, here the orderPizza() function returns a Promise, which in turn takes a callback with two parameters, resolve and reject.

**Resolve** is called when the asynchronous operation we were performing was successfull, and **Reject**, when it failed.

So this is how a Promise is constrcuted, now let's see how to consume them.

```
orderPizza('Margherita')
  .then( pizza =&amp;amp;gt; {
    const toppings = addToppping('chillyflakes');
    return { pizza:pizza , toppings:toppings };
  })
  .then( foodItems =&amp;amp;gt; {
    console.log('Here's the food!', foodItems)
  })
  .catch( err =&amp;amp;gt; {
    console.log(err)
  })
 ```

Instead of passing in a callback function, we called a *.then* function on the return value of the host function. This .then function usually gives us access to the actions to be performed upon completion of the Promise. To handle errors, we add a *.catch* call on the result and that gives us access to an error when it happens.

#### Few Quirks about Promises

- the *then* keyword also returns a Promise. The returned Promise resolves to the value the handler function returns. 
- This is why Promise can be chained. In the example, a second *then* was appended to the first *then*. It takes the fooditems and displays them. 
- The main advantage of Promise is that it simplifies the use of asynchronous functions. Instead of passing around callbacks, Promise based functions looks like regular functions- they take inputs as arguments and returns an output. The only difference being that the output might take some time to be available, or it might result in some error.

But even after using Promises and .then, things can get messy. Although Promise interfaces are a step forward from callbacks, the ES8 standard introduces async/await, a new syntactic sugar over Promises to make asynchronous code as readable as synchronous code. The next article in this series will talk about async/await and its advantages over Promises in detail.





