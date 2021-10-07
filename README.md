let fs = require('fs');
let text;
let alphabet = new Array();
let i=0,  entropy=0, alphLen = 0;
 
text = fs.readFileSync('inputent.txt');
text = text.toString();
for (i=0; i < text.length; i++){
	alphabet[text.charAt(i)] = 0;
} 
 
for (i=0; i < text.length; i++){
    alphabet[text.charAt(i)]++; 
}
 
for (i in alphabet){
    alphabet[i] /= text.length;
    alphLen++;
}
if (alphLen <= 1){
    entropy = 0;
}
else{
    for (i in alphabet){
        entropy -= alphabet[i] * Math.log2(alphabet[i])/ Math.log2(alphLen);
    }
}
console.log(entropy);
