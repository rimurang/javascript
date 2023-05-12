<br><br>

## 배열의 평균값

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/120817" target="_blank" title="배열의 평균값">https://school.programmers.co.kr/learn/courses/30/lessons/120817</a>

#### ▶ 문제 설명
정수 배열 numbers가 매개변수로 주어집니다. <b>numbers의 원소의 평균값</b>을 return하도록 solution 함수를 완성해주세요.
* numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
* result = 5.5
<br>

#### ▶ 제한
* 0 ≤ numbers의 원소 ≤ 1,000
* 1 ≤ numbers의 길이 ≤ 100
* 정답의 소수 부분이 .0 또는 .5인 경우만 입력으로 주어집니다.


```Javascript
function solution(numbers) {
    
    const numLeng = numbers.length; // numbers 배열의 길이 
    let numSum = 0; // 합을 위한 변수
    
    for( var i = 0 ; i < numLeng ; i++ ){ // i 가 0부터 9까지 1씩 오르며 반복
        numSum += numbers[i]; // 배열의 순서대로 값을 더하며 numSum에 대입
    }
    
    return numSum/numLeng; // numSum을 numLeng으로 나누고 평균 구하기 
    
}
```

#### ▼ forEach로 바꿔보기

```Javascript
function solution(numbers) {
    
    const leng = numbers.length;
    let nSum = 0;    

    numbers.forEach(function(idx){
        nSum += idx;
    })
    
    return nSum/leng;
}
```

<br><br>
<hr>
<br><br><br>

## 7의 개수

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/120912" target="_blank" title="배열의 평균값">https://school.programmers.co.kr/learn/courses/30/lessons/120912</a>

#### ▶ 문제 설명
머쓱이는 행운의 숫자 7을 가장 좋아합니다. 정수 배열 array가 매개변수로 주어질 때, <b>7이 총 몇 개 있는지</b> return 하도록 solution 함수를 완성해보세요.
* array = [7, 77, 17]
* result = 4
<br>

#### ▶ 제한
* 1 ≤ array의 길이 ≤ 100
* 0 ≤ array의 원소 ≤ 100,000


```Javascript
function solution(array) {
    
    const arrayLeng = array.length; // array 배열의 길이 
    let arraySum = 0; // 답을 위한 변수
    
    for ( var i = 0 ; i < arrayLeng ; i++ ) {
        
        let arrayStr = String(array[i]); // 숫자를 문자로 변환
        let arraySpl = arrayStr.split(''); // 문자열 자르기
        let arraySplLeng = arraySpl.length; // 문자열로 자른 배열 개수
        
        for ( var v = 0 ; v < arraySplLeng ; v++ ) { // arraySplLeng 배열 개수만큼 반복
            
            if (arraySpl[v] === '7') { // arraySpl 배열에 '7' 찾기
                arraySum++; // '7'있으면 ++
            }
            
        }
        
    }
    
    return arraySum;
}
```

#### ▼ filter 사용, 간략하게 바꿔보기

```Javascript
function solution(numbers) {
    
    const result = array.join('').split('').filter(v => v === '7').length;

    return result;
    
}
```

<br><br>
<hr>
<br><br><br>

## 문자열 섞기

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/181942" target="_blank" title="문자열  섞기">https://school.programmers.co.kr/learn/courses/30/lessons/181942</a>

#### ▶ 문제 설명
길이가 같은 두 문자열 str1과 str2가 주어집니다.<br>
두 문자열의 각 문자가 앞에서부터 서로 번갈아가면서 한 번씩 등장하는 문자열을 만들어 return 하는 solution 함수를 완성해 주세요.
* str1 = "aaaaa"
* str2 = "bbbbb"
* result = "ababababab"
<br>

#### ▶ 제한
* 1 ≤ str1의 길이 = str2의 길이 ≤ 10
* str1과 str2는 알파벳 소문자로 이루어진 문자열입니다.


```Javascript
function solution(str1, str2) {
    
    let str1Spl = str1.split(''); // 배열(문자열)로 자르기 
    let str2Spl = str2.split(''); // 배열(문자열)로 자르기
    
    const str1Leng = str1.length; // 배열개수 구하기
    const str2Leng = str2.length; // 배열개수 구하기
    
    let strArray = ""; // 외부 변수 선언
    
    for ( var i = 0 ; i < str1Leng ; i++ ) { // str1 개수만큼 반복
        strArray += ( str1Spl[i] + str2Spl[i] );
    }
    
    return strArray;
}
```

#### ▶ 해설
* += 의 활용
* 숫자열 + 문자열은 문자열이 된다
* 문자열 + 문자열은 문자열이 된다


<br><br>
<hr>
<br><br><br>

## 중복된 숫자 개수

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/120583" target="_blank" title="문자열  섞기">https://school.programmers.co.kr/learn/courses/30/lessons/120583</a>

#### ▶ 문제 설명
정수가 담긴 배열 array와 정수 n이 매개변수로 주어질 때, array에 n이 몇 개 있는 지를 return 하도록 solution 함수를 완성해보세요.
* array = [1,2,3,4,5]	
* n = 1	
* result = 2
* array = [0,2,3,4]	
* n = 1	
* result = 0
<br>

#### ▶ 제한
* 1 ≤ array의 길이 ≤ 100<br>
* 0 ≤ array의 원소 ≤ 1,000<br>
* 0 ≤ n ≤ 1,000


```Javascript
function solution(array, n) {
    // filter로 찾기 
    let answer = array.filter(i => i === n).length;
    return answer;
}
```

#### ▶ 해설
* filter로 1을 찾는다.

#### ▼ 화살표함수로 간략하게

```Javascript
const solution = (array, n) => array.filter(i => i === n).length;
```

<br><br>
<hr>
<br><br><br>

## 배열 원소의 길이

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/120854" target="_blank" title="문자열  섞기">https://school.programmers.co.kr/learn/courses/30/lessons/120854</a>

#### ▶ 문제 설명
문자열 배열 strlist가 매개변수로 주어집니다. strlist 각 원소의 길이를 담은 배열을 retrun하도록 solution 함수를 완성해주세요.
* strlist = ["We", "are", "the", "world!"]		
* result = [2, 3, 3, 6]	
* strlist = ["I", "Love", "Programmers."]		
* result = [1, 4, 12]	
<br>

#### ▶ 제한
* 1 ≤ strlist 원소의 길이 ≤ 100 <br>
* strlist는 알파벳 소문자, 대문자, 특수문자로 구성되어 있습니다.


```Javascript
function solution(strlist) {
    
    let splArr = [];// 변수 배열 선언
    
    strlist.forEach(function(idx){
        splArr.push(idx.length);
        // ? : splArr += idx.length
        // ? : console.log(typeof splArr)
    })
    
    return splArr;
}
```
#### ▶ 해설
* 변수 배열, 스트링 선언 구분 학습
* 스트링 length는 글자수를 체크함
* +=와 push 차이 알아두기


```Javascript
function solution(strlist) {
    return strlist.map(v => v.length)
}
```

#### ▶ 해설
* map은 리턴이 필요함. 없을경우 undefined


```Javascript
const solution = (strlist) => strlist.map(v => v.length)
// return 정답!
//화살표 함수는 return이 생략되어있음

const solution = (strlist) => strlist.map(v => {v.length})
// return undefined
// 리턴값이 없기때문

const solution = (strlist) => strlist.map(v => {return v.length})
// return 정답!
// 리턴값이 있기때문
```

#### ▶ 해설
* 화살표함수에는 return이 생략되어있음




<br><br>
<hr>
<br><br><br>

## 아이스 아메리카노

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/120819" target="_blank" title="문자열  섞기">https://school.programmers.co.kr/learn/courses/30/lessons/120819</a>

#### ▶ 문제 설명
머쓱이는 추운 날에도 아이스 아메리카노만 마십니다. 아이스 아메리카노는 한잔에 5,500원입니다. 머쓱이가 가지고 있는 돈 money가 매개변수로 주어질 때, 머쓱이가 최대로 마실 수 있는 아메리카노의 잔 수와 남는 돈을 순서대로 담은 배열을 return 하도록 solution 함수를 완성해보세요.
* money = 5,500
* result = [1, 0]
* money = 15,000
* result = [2, 4000]
<br>

#### ▶ 제한
* 0 < money ≤ 1,000,000


```Javascript
function solution(money) {
    
    const coffeePrice = 5500;
    let coffeeNum = Math.floor(money / coffeePrice);
    let coffeeChg = money % coffeePrice;
    
    var answer = [coffeeNum,coffeeChg];
    return answer;
}
```

#### ▶ 해설
* --



<br><br>
<hr>
<br><br><br>

## 양꼬치 집

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/120830" target="_blank" title="문자열  섞기">https://school.programmers.co.kr/learn/courses/30/lessons/120830</a>

#### ▶ 문제 설명
머쓱이네 양꼬치 가게는 10인분을 먹으면 음료수 하나를 서비스로 줍니다. 양꼬치는 1인분에 12,000원, 음료수는 2,000원입니다. 정수 n과 k가 매개변수로 주어졌을 때, 양꼬치 n인분과 음료수 k개를 먹었다면 총얼마를 지불해야 하는지 return 하도록 solution 함수를 완성해보세요.
* n = 10
* k = 3
* result = 124,000
* n = 64
* k = 6
* result = 768,000
<br>

#### ▶ 제한
* 0 < n < 1,000
* n / 10 ≤ k < 1,000
* 서비스로 받은 음료수는 모두 마십니다.

```Javascript
function solution(n, k) {
    
    let drinkPrice = (k - Math.floor(n/10)) * 2000;
    // 지불할 음료수 총액
    // 먹은 음료 k개에서 서비스로 받은 개수를 빼고 가격을 곱함
    let lambNumber = n*12000;
    // 지불할 양고기 총액
    // 먹은 양고기 n인분에 가격을 곱함
    
    return drinkPrice+lambNumber;
}
```

#### ▼ 화살표함수로 

```Javascript
const solution = (n,k) => {
    
    let drinkPrice = (k - Math.floor(n/10)) * 2000;// 지불할 음료수 총액
    let lambNumber = n*12000;//지불할 양고기 총액

    return drinkPrice+lambNumber;
    
}
```


