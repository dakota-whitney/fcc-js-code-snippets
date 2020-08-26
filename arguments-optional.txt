function addTogether(x) {
  let isNum = num => typeof num === 'number';

  if (arguments.length >= 2) {
    if ((isNum(arguments[0])) && (isNum(arguments[1]))) {
      return arguments[0] + arguments[1];
    }
  } else {
   if (isNum(x)) {
     return function(y) {
       if (isNum(y)) {
         return x + y;
       }
     }
   }
  }
  return undefined;
}

addTogether(5)(7);
