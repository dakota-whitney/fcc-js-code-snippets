function rangeOfNumbers(startNum, endNum) {
  if (startNum > endNum) {
    return [];
  } else {
const recArray = rangeOfNumbers(startNum + 1, endNum);
recArray.unshift(startNum);
return recArray;
  }
};
