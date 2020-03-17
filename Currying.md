# Currying

//Normal
function addThreeNumbers = (a, b, c) => {
  return a + b + c;
}

//Curried

const greetDeeplyCurried = function(greeting) {
  return function(separator) {
    return function(name)  {
       return function(emphasis){
        console.log(greeting + separator + name + emphasis);
      };
    };
  };
};

greetDeeplyCurried("Hello")(" ")("AJ")("!");
