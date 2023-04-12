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



<hr>

<br><br>
