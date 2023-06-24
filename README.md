# Interview Preperation Day 4
## Q1. What are function constructors?
- A function constructor is a way to create a object using a function as a blue print or template.
- it allow you to define a reusable structure for creating multiple object with similar properties and method.

## Q2. Explain call(), apply() and, bind() methods. Give an example of call(), apply(), bind().
These all three methods are used to invoke a function where we are supposed to pass an object as first argument and at the time of definition we don't have mention this object as a parameter and we can access the values of object by using this keyword in function definition.
- Call : The call method is used to invoked a function with a specific 'this' value, and arguments provide individuly. The call() method invokes a function in which first argument will be the object and rest of the arguments required by function will be provided as an individual arguments.

- Apply : Apply is similar with call, but take argument as an array. The apply() method invokes a function in which first argument will be the object and rest of the arguments will be passed as an array of elements.

- Bind - Bind is a function that helps you create another function that you can execute later with the new context of this that is provided. The bind() method returns a new function and this function will be having the reference of the object passed, now whenever you want to use this returned function in the code you can use it by passing rest of the arguments.
##  
    Example:
    const Person1 = {
        name: "EA23",
        course : "MEAN",
        age: 24
    }

    function Display(greet, greet1){
        console.log(`${this.name} : ${this.age} : ${this.course} : ${greet} : ${greet1}`);
    }

    Display.call(Person1, "Call", "Good Evening...")
    Display.apply(Person1, ["Apply", "Good Evening..."]);
    let result = Display.bind(Person1, "Bind", "Good Evening...");
    result();

## Q3. What is the purpose of async/await keywords?
An async function is a function declared with the async keyword, and the await keyword is permitted within it. The async and await keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need promise chains.
## Q4. Explain prototypes.
The prototype is an object that is associated with every JavaScript object. It serves as a blueprint or template for creating new objects through inheritance. The prototype object contains properties and methods that are shared among all instances created from it.
## Q5. What is prototype chain.
In Promise Chaining we use more than one .then method in a single function.

    Example:
    function mypromise(alpha, timeout){
        return new Promise((resolve, reject)=>{
            setTimeout(() => {
                console.log(alpha)
                resolve("Promise resolved")
            }, timeout)
        })
    }

    function call(){
        mypromise("A",1000)
        .then(() => mypromise("E",2000) )
        .then(() => mypromise("I",3000) )
        .then(() => mypromise("O",4000) )
        .then(() => mypromise("U",5000) )
    }
    call()
## Q6. Give an example of inheritance using function constructor.

    Code:
    function Animal(name){
        this.name = name;
    }

    Animal.prototype.sayHello = function(){
        console.log(`My name is : ${this.name}`)
    }

    // Inherit from Animal
    Dog.prototype = Object.create(Animal.prototype)

    // // Child class
    function Dog(name, breed){
        Animal.call(this, name);
        this.breed = breed
    }
    // Add new method to Dog Object
    Dog.prototype.bark = function(){
        console.log('Woof!!')
    }

    // Create instaance of animal and Dog
    var animal = new Animal('Indian Dog')
    var dog = new Dog('Puppy', 'German')

    dog.bark()
    dog.sayHello()