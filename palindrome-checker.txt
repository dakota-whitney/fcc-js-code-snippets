function palindrome(str) {
  let regex = /[A-Za-z0-9]/gi;
  let strArr = str.toLowerCase().split("");
  strArr = strArr.filter(char => char.match(regex))
  for (let i = 0; i < strArr.length; i++) {
    if (strArr[i] !== strArr[(strArr.length - 1) - i]) {
      return false;
    }
  }
  return true;
}



palindrome("0_0 (: /-\ :) 0-0");
