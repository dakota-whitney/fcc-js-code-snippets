function rot13(str) {
  let decoded = "";
  const regex = /\w/i;
  for (let i = 0; i < str.length; i++) {
    if (regex.test(str.charAt(i))) {
      if (str.charCodeAt(i) > 77) {
        decoded = decoded.concat(String.fromCharCode(str.charCodeAt(i) - 13));
      } else if (str.charCodeAt(i) <= 77) {
        decoded = decoded.concat(String.fromCharCode(str.charCodeAt(i) + 13));
      };
    } else {
    decoded = decoded.concat(str.charAt(i));
    };
  };
  return decoded;
};

rot13("SERR PBQR PNZC");
