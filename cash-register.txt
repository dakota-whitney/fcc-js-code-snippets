function checkCashRegister(price, cash, cid) {
  //Object initialization for eventual output
  let register = {
    "status":"",
    "change":[],
  };

  //Object for string/currency conversion
  const currency = {
    "PENNY": .01,
    "NICKEL": .05,
    "DIME": .10,
    "QUARTER": .25,
    "ONE": 1,
    "FIVE": 5,
    "TEN": 10,
    "TWENTY": 20,
    "ONE HUNDRED": 100
  };

  //Coins array to check for insufficient bill amount
  const coins = cid.slice(0,4);

  //Get sum of all of cid's dollar amounts
  let totalCash = cid.reduce((total,arr) => {
    return Math.round((total += arr[1]) * 100) / 100;
  },0)

  //Get change due
  let changeDue = cash - price;

//If we don't have enough total cash OR we don't have sufficient bills
if (changeDue > totalCash || ((Object.values(currency).every(denom => changeDue % denom < 1)) && (coins.every(arr => arr[1] < changeDue)))) {
    register.status = "INSUFFICIENT_FUNDS";
 } 
 
 //If we have just enough change
 else if (changeDue == totalCash) {
   register.status = "CLOSED";
   register.change = cid;
 } 
 
 //If we need to give change
 else {
   register.status = "OPEN";
   //Remove bills that are too high from calculations
   register.change = cid.filter(arr => changeDue > currency[arr[0]]);
    //Iterate through array starting at the end
    for (let i = register.change.length - 1; i >= 0; i--) {
      //Initialize currency conversion variable
      let denom = currency[register.change[i][0]];
      //If we have enough of the current denomination, find maximum amount of bills needed
      if (changeDue < register.change[i][1]) {
        register.change[i][1] = Math.floor(changeDue / denom) * denom;
      };
      //Subtract the current change due from the register
      changeDue -= register.change[i][1];
      //Round to nearest hundredth
      changeDue = Math.round(changeDue * 100) / 100;
    }
    //Removing unnecessary denominations and displaying from highest to lowest
  register.change = register.change.filter(arr => arr[1] !== 0).reverse();
 }
  return register;
}

checkCashRegister(19.5, 20, [["PENNY", 0.5], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]]);