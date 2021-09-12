# Destructuring (구조 분해 문법)

: 객체나 배열을 변수로 분해할 수 있게 해주는 문법

```JS
let arr = ["abc","def"];
let [first, second] = arr; //배열 분해

console.log(first); // "abc"
console.log(second); // "def"


let person = {
    name: "yun"
    age: 22;
}

let {a,b} = person; //객체 분해


```

