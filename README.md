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

