# JavaScript-Interview-Prep-Functions-Closures-Currying


https://www.youtube.com/watch?v=tbqVqP5ilzQ

https://raw.githubusercontent.com/RodrigoMvs123/JavaScript-Interview-Prep-Functions-Closures-Currying/main/README.md

https://github.com/RodrigoMvs123/JavaScript-Interview-Prep-Functions-Closures-Currying/blame/main/README.md

script.js
//Functions in JavaScript
//Q1 - What are Function Declarations?

function square(num) {
      return num * num;
}

//Functions in JavaScript
//Q2 - What is Function Expression ?
 
const square = function (num) {
      return num * num;
}

console.log(square(5));

//Functions in JavaScript
//Q3 - What are First Class Functions? 


function square(num) {
      return num * num;
}

function displaySquare(fn) {
      console.log(“Square is ” + fn(5));
}

displaySquare(square)

//Functions in JavaScript
//Q4 - What is IIFE?

(function square(num) {
      console.log( num * num );
}
)(5);

//Functions in JavaScript
//Q5 - IIFE - O/P Based Question? 

(function (x) {
    return (function (y) {
       console.log(x); // 1
})(2);
})(1);

//Functions in JavaScript
//Q6 - Function Scope

-https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions

// The following variables are defined in the global scope
const num1 = 20;
const num2 = 3;
const name = "Chamakh";

// This function is defined in the global scope
function multiply() {
  return num1 * num2;
}

console.log(multiply()); // 60

// A nested function example
function getScore() {
  const num1 = 2;
  const num2 = 3;

  function add() {
    return `${name} scored ${num1 + num2}`;
  }

  return add();
}

console.log(getScore()); // "Chamakh scored 5"

//Functions in JavaScript
//Q7 - Function Scope - O/P Based Question 

for (let i=0; i<5; i++) {
   setTimeout (function () {
      console.log(i);
}, i * 1000);
}

//Functions in JavaScript
//Q8 - Function Hoisting 

functionName();

function functionName() {
      console.log(x);
      var x = 5; 

      console.log(“Roadside Coder”);
}

//Functions in JavaScript
//Q9 - Function Hoisting - O/P Based Question

var x = 21;

var fun = function () {
     console.log(x);
     var x = 20;
};

fun();

//Functions in JavaScript
//Q10 - Params vs Arguments 

function multiply(...nums) { 
     console.log(nums[0] * nums[1]);
}
var arr = [5,6]
multiply(...arr);

//Functions in JavaScript
//Q11 - Params vs Arguments - O/P Based Question 

const fn = (a, x, y, ….numbers) => {
console.log(x,y, numbers)
};

fn(5, 6, 3, 7, 8, 9)

//Functions in JavaScript
//Q12 - Callback Function 

document.addEventListener(“click”, function (params) {
        
})

//Functions in JavaScript
//Q13 - Arrow Functions
const add = (firstNum, secondNum) => {
    return firstNum + secondNum;
};

//Functions in JavaScript
//Q14 - Arrow Functions vs Regular Function 

// 1 - Syntax 
function square(num) {
    return num * num; 
}

const square = (num) => {
    return num * num;
};

// 2 - Implicit “return” keyword
const square = (num) => num * num;

// 3 - Arguments 
function fn() {
    console.log(arguments);
}

fn(1, 3, 2);

// const fnArr = () => {
//       console.log(arguments);
//}
//    fnArr(1, 3, 2);

// 4 - “this” keyword
let user = {
    username: “Roadside Coder”, 
    rc1: () => {
      console.log(“Subscribe to” + this.username);
},
    rc2: () {
      console.log(“Subscribe to” + this.username);
},
};

user.rc1();
user.rc2();



//Closures in JavaScript
//Lexical Scope

var name = “RoadsideCoder”;

// Global Scope
function local () {
      // Local Scope
   console.log(username);
}

local();

// global scope
function subscribe() {
      var name = “Roadside Coder”;
     // inner scope 2
      function displayName() {
     // inner scope
          alert(name);
}
    displayName();
}
subscribe();

//Closures in JavaScript
// What is a closure? 

function makeFunc() {
  const name = "Mozilla";
  function displayName() {
    console.log(name);
  }
  return displayName;
}

const myFunc = makeFunc();
myFunc();

//Closures in Javascript
//Closure Scope Chain 

// global scope
const e = 10;
function sum(a) {
  return function (b) {
    return function (c) {
      // outer functions scope
      return function (d) {
        // local scope
        return a + b + c + d + e;
      };
    };
  };
}

console.log(sum(1)(2)(3)(4)); // 20

//Closures in Javascript
// Ques 1: What will be logged to console? 

let count = 0;
(function printCount() {
  if (count === 0) {
    let count = 1; //shadowing
    console.log(count); //1
}
   // count = 0
  console.log(count); // 0
})();

//Closures in Javascript
// Ques 2: Write a function that would allow you to do this

function createBase(num) {
     return function (innerNum) {
         console.log (innerNum + num);
    };
}

var addSix = createBase(6);
addSix(10); // returns 16
addSix(21); // returns 27

//Closures in Javascript
// Ques 3: Time Optimization 

function find(index) {
     let a = [];
     for (let i =0; i <1000000; i ++) {
        a[i] = i * i;
}

return function (index) {
console.log(a[index]);
    };
}

const closure = find();
console.time(“6”);
find(6);
console.timeEnd(“6”);
console.time(“50”);
closure(“50”);
console.timeEnd(“50”);

//Closure in Javascript 
// Ques 4: Block scope and setTimeout


for ( var i =0; i < 3; i ++ ) {

function inner(i) {
        setTimeout (function log() {
    console.log(i); // what is logged ? 
}, i * 1000);
}

inner(i);
}

//Closure in Javascript 
// Ques 5: How would you use a closure to create a private counter? 

function counter() {
     var_counter = 0;

function add(increment) {
         _counter += increment;
}
function retrive() {
      return “Counter =” + _counter;
}
return {
   add, 
   retrieve,
};
}

const c = counter();
c.add(5);
c.add(10);

console.log(c.retrive());

//Closure in Javascript 
// Ques 6: What is Module Pattern ?

var Module = ( function () {
    function privateMethod () {
       // do something 
         console.log(“private”);
}

   return {
       publicMethod: function () {
         console.log(“public”);

},
};

})();

Module.publicMethod();
Module.privateMethod();

//Closure in Javascript 
// Ques 7: Make this run only once

let view;
function likeTheVideo() {

   let called = 0;

   return function () {
    if (called > 0 ) {
    console.log(“Already subscribed to Roadside Coder”);
} else {
        view = “Roadside Coder”;
             console.log(“Subscribe to”, view);
             called++;
}
};
}

let isSubscribed = likeTheVideo();

isSubscribed();

//Closure in Javascript 
// Ques 8: Once Pollyfill

function once(func, context) {
    let ran;
    
    return function() {
         if (func) {
            ran = func.apply(context || this, arguments);
            func = null;
            }

            return ran;  
     };
}

const hello = once ((a,b) console.log(“hello” a, b));

hello(1, 2);
hello();

//Closure in Javascript 
// Ques 9: Memoize Pollyfill
// Question 3: Implement Caching/Memoize Function 

function myMemoize (fn) {
      const res = {};
      return function ( …args) {
            var argsCache = JSON.stringify(args);
            if(!res[argsCache]) {
               res[argsCache] = fn.call(context || this, …args);
        }
        return res [argsCache];
    };
   }
  


const clumsyProduct = (num1, num2) => {
     for ( let i = 1, i <= 10000000; i++) {}

     return num1 * num2;
};

const memoizedClumsyProduct = myMemoize(clumsyProduct);

console.time(“First call”);
console.log( memoizedClumsyProduct(9467, 7649));
console.timeEnd(“First call);

console.time(“Second call”);
console.log( memoizedClumsyProduct(9467, 7649));
console.timeEnd(“Second call);

//Currying in Javascript 
// Exemple f(a, b) into f (a) (b)

function f(a) {
     return function(b) {
          return ‘${a} ${b}’;
     } 
}

console.log(f(5)(6));

//Currying in Javascript 
// Question 1 - sum (2)(6)(1)

function sum(a,b,c) {
      return a+b+c;
}

console.log(sum(2,6,1));

function sum(a) {
    return function (b) {
         return function ( c ) {
               return a+b+c;
       }
   }
}

console.log(sum(2)(6)(1));

//Currying in Javascript 
// Question 2 - 
evaluate(“sum”)(4)(2) => 6
evaluate(“multiply”)(4)(2) => 8
evaluate(“divide”)(4)(2) => 2
evaluate(“substract”)(4)(2) => 2

function evaluate (operation) {
     return function (a) {
         return function (b) {
              if(operation === “sum”) return a+b;
              else if (operation === “multiply”) return a * b;
              else if (operation === “divide”) return a/b;
                 else if (operation === “substract”) return a - b;
                  else  return “Invalid Operation”;
    }
  }
}

console.log(evaluate(“sum”)(4)(2)); 

const mul = evaluate(“multiply”);

console.log(mul(3)(5)); // 15
console.log(mul(2)(6); // 12

//Currying in Javascript 
// Question 5: Infinite Currying 

function add(a) {
      return function (b) {
         if(b) return add(a+b);
         return a;
    };
}

console.log(add(5)(2)(4)(8)());

//Currying in Javascript 
// Question 4 - Currying vs Partial Application 

function sum(a) {
     return function (b,c) {
          return a+b+c;   
     }
}

const x = sum(10);

console.log(x(5,6));
console.log(x(3,2));

//or

console.log(sum(20)(1,4));

//Currying in Javascript 
// Question 5 - Manipulating DOM 

function updateElementText(id) {
    return function (content ) {
       document.querySelector(“#” + id).textContent = content;
};
}

const updateHeader = updateElementText(“heading”)

updateHeader(“Hello RoadsideCoder”);

// Currying in Javascript 
// Question 6 - curry() implementation 
// Converts f(a,b,c) into f(a)(b)(c) 

function curry(func) {
     return function curriedFunc (...args) {
   //   console.log(args.lenght,func.lenght);
        if (args.lenght >= func.lenght) {
            return func(...args);
} else {
  return function (...next) {
      return curriedFunc (...args, …next);
          };
       }
    };
}

const sum = (a,b,c,d) => a+b+c+d;

const totalSum = curry(sum);

console.log(totalSum(1)(6)(5)(6));
