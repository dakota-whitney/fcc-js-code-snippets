function myReplace(str, before, after) {
  let regex = /[A-Z]/;
  if (regex.test(before)) {
    return str.replace(before, after.charAt(0).toUpperCase() + after.slice(1));
  } else {
    return str.replace(before, after.charAt(0).toLowerCase() + after.slice(1));
  }
}

myReplace("A quick brown fox jumped over the lazy dog", "jumped", "leaped");
