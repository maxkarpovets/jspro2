# Higher order functions

```
var paint = function(original, replacement, source) {
  return function(source) {
    return source.replace(original, replacement);
  };
};
 
var makeWhite = paint("Black", "White");
var makeBlack = paint("White", "Black");
 
console.log(makeWhite("Color is Black"));
console.log(makeBlack("Color is White"));
```
# Curring
```
var feed = function(food) {
  return function(pet) {
    console.log( `${ pet} eats ${ food}`);
  };
};

var doFeed = feed("meat");

doFeed("Dog");
doFeed("Cat");
feed("apple")("Horse"); 
```
# Classes
```
class Animal {
  constructor(legs, color) {
    this.name = 'Animal';
    this.legs = 4;
    this.color = 'red';
  }

  sayName() {
    console.log(`My name is ${this.name}`);
    console.log(`I have ${this.legs} legs `);
    console.log(`My color is  ${this.color}`);
  }
}

class Cat extends Animal {
  constructor(name, legs, color) {

    super();
    this.name = name;
    this.color = color;
  }


  sayName2() {
    console.log(`My name is ${this.name}`);
  }
}

let murchik = new Cat('MyCat',4,'white');
murchik.sayName();
murchik.sayName2();
```

# Http/Promise

```
/*
let request = obj => {
   return new Promise((resolve, reject) => {
       let xhr = new XMLHttpRequest();
       xhr.open(obj.method || "GET", obj.url);
       if (obj.headers) {
           Object.keys(obj.headers).forEach(key => {
               xhr.setRequestHeader(key, obj.headers[key]);
           });
       }
       xhr.onload = () => {
           if (xhr.status >= 200 && xhr.status < 300) {
               resolve(xhr.response);
           } else {
               reject(xhr.statusText);
           }
       };
       xhr.onerror = () => reject(xhr.statusText);
       xhr.send(obj.body);
   });
};

request({url: "https://jsonplaceholder.typicode.com/users"})
   .then(data => {
       let employees = JSON.parse(data);
       renderData(employees)

   })
   .catch(error => {
       console.log(error);
   });


function renderData(data) {
  let html = "";
  data.forEach(employee => {
      html += `
          <div>
              <div>
                  ${employee.name} ${employee.username}
                  <p>${employee.email}</p>
                  --------
              </div>
          </div>`;
  });
  document.getElementById("list").innerHTML = html;
}

*/
var promise = new Promise(function(resolve, reject) {
    let someData = [1,2,3];
    resolve(someData);
    reject(Error("It broke"));
});

promise.then(function(result) {
  console.log(result); // "Stuff worked!"
}, function(err) {
  console.log(err); // Error: "It broke"
});
```

# Singleton
```
var Singleton = (function () {
    var instance;
 
    function createInstance() {
        var object = new Object("I am the instance");
        return object;
    }
 
    return {
        getInstance: function () {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        }
    };
})();
 
function run() {
 
    var instance1 = Singleton.getInstance();
    var instance2 = Singleton.getInstance();
 
    alert("Same instance? " + (instance1 === instance2));  
}
```

#  Chain of Responsibility
```
function CustomerPrototype(proto) {
    this.proto = proto;
 
    this.clone = function () {
        var customer = new Customer();
 
        customer.first = proto.first;
        customer.last = proto.last;
        customer.status = proto.status;
 
        return customer;
    };
}
 
function Customer(first, last, status) {
 
    this.first = first;
    this.last = last;
    this.status = status;
 
    this.say = function () {
        alert("name: " + this.first + " " + this.last +
              ", status: " + this.status);
    };
}
 
function run() {
 
    var proto = new Customer("n/a", "n/a", "pending");
    var prototype = new CustomerPrototype(proto);
 
    var customer = prototype.clone();
    customer.say();
}
```

# Tasks
## 1.
Реалізувати, функцію, яка буде до вхідного числа додавати 10.

## 2.
Написати массив даних, який буде повертатись промісом якщо висота скріну (screen ) більше 1000, і помилку, якщо менше

## 3.
Реалізувати "гаманець" ( можна додавати і віднімати гроші) за допомогою Chain of Responsibility

# Homework
## 1
Створіть батьківський клас Product, який буде приймати 2 аргументи (назва і ціна). Усередині класу зробіть перевірку на випадок якщо ціна буде нижче 0 в повідомленні виведіть ім'я товару і оповіщення про те що товар (ім'я товару) не можна створювати з негативною ціною. Також створіть 2 підкласи - Food і Toy які будуть наслідувати клас продукту, а також мати власну властивість (їжа та іграшка).

## 2 
Створити юзера, в локалсторедж, і діставати його в аплікуху за допомогою паттерну Singleton

## 3 
 
Реалізувати методи Post/Put/Delete для api, за допомогою  XMLHttpRequest
https://github.com/typicode/jsonplaceholder#how-to
