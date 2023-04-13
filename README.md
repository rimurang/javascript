# 공부내용 정리

<br><br>

▶ 함수호출
<ul>
  <li>함수가 호출되면 호출된 함수의 선언부로 가서 코드를 읽는다.</li>
  <li>선언부가 닫히는 부분을 만나야  해당 함수호출은 끝난다.</li>
</ul>

<br><br>

## 스택

<img src="https://user-images.githubusercontent.com/45233490/224595233-f5bc42cd-ade1-40ee-aee9-1a7b80b4dd48.png" width="200"/>

<ul>
  <li>밑에서부터 하나씩 쌓이고, 위에서부터 하나씩 빠져나간다 ( = 명함쌓기, 명함빼기)</li>
  <li>LIFO(Last In First Out), FILO(First In Last Out)</li>
</ul>

<br><br>

## 큐

<img src="https://user-images.githubusercontent.com/45233490/224595288-4fad6a0c-a576-4388-8617-481168cbd38e.png" width="300"/>

<ul>
  <li>먼저 들어온것이 먼저 나간다. ( = 편의점 음료수 선입선출..)</li>
  <li>FIFO(First In First Out)</li>
</ul>


<br><br>


```Javascript

const x = 'x';
function c() { 
  const y = 'y';
  console.log('c');
} 

function a() { 
  console.log('a');
  function b() { 
    const z = 'z';
    console.log('b');
    c();
  } 
  b(); 
}

a(); // a, b, c
c(); // c

```
<ul>
  <li>함수의 선언과 호출을 구분하기!</li>
  <li>함수가 호출되면 선언부('{ ~ }')가 실행됨</li>
</ul>


<br><br><br>
<hr>
<br><br><br>





## 스코프 체인
- 함수에서 어떤 값에 접근이 가능/불가능 한가 
- 스코프=선언 
- 블록 기준


!!! 블록이라 함은?

```Javascript

// 함수 선언 블록
function a() { } 

// if문 블록
if () { }

// for문 블록
for () { }

// while문 블록
while () { }

// switch문 블록
switch () { }

// 화살표 함수 블록
const a () => {}

```



#### ▶ 스코프 체인 분석하는 방법
```Javascript

const x = 'x';
function c() { 
  const y = 'y';
  console.log('c');
  function b() { 
    const z = 'z';
    console.log('b');
    c();
  } 
} 

function a() { 
  console.log('a');
  b(); 
}

a();  //  콘솔 에러 b is not defined
c();

```



부모함수에 포함되어있는지 확인하기 (선언지도 그려보기, 선언 좌측 구분선 타고타고 올라가기)
<br><br>
#### [선언 분석] <br>
● a에서 b에 접근 가능한가? (정답: X) <br>

##### a > anonymous <br>

1. a 안에 b 없음 <br>
2. anony 안에 b 없음 <br><br>


● b에서 a에 접근 가능한가? (정답: O)  <br>

##### b > c > anonymous <br>

1. b 안에 a 없음 <br>
2. c 안에 a 없음 <br>
3. anony 안에 a 있음 <br>

<br><br><br>
<hr>
<br><br><br>

## this
this 는 기본적으로 window
#### this 는 함수가 호출될때 정해짐

```Javascript

function a() { 
  console.log(this);
}
a();  //  window

js // window, globalThis
node // global, globalThis
// 최근 스펙에서 js, node 둘다 globalThis로 합쳐짐

```
↑ 콘솔로 this 찍어보기



#### ▶ this 예제

```Javascript

const obj = {
  name: 'rimurang'
  sayName(){
    console.log(this.name);
  }
};
obj.sayName(); 
// rimurang , 여기서 this는 obj
// 나(this)는 obj야~

const sayN = obj.sayName();
sayN(); // '', 여기서 this는 window

```
```Javascript

const obj = {
  name: 'rimurang'
  sayName: () => {
    console.log(this.name);
  }
};
obj.sayName(); // '' , 여기서 this는 window
// 화살표 함수이면 this는 window

```

#### ▶ this가 바뀌는 경우
<ul>
  <li>호출때 함수앞에 obj. 와 같은 객체가 붙는 경우</li>
  <li>new 붙여서 호출</li>
  <li>.bind, .apply, .call 사용해서 this를 직접적으로 바꿔준 경우</li>
  <li>- .bind (this만 바뀌는 새로운 함수를 만들어줌)</li>
  <li>- .apply (bind 기능에서 선언까지 해줌)</li>
  <li>- .call (applt와 함수 호출하는 방법만 다름 (매개변수를 apply는 배열(array)로, call은 순서대로)) </li>
  <li>화살표 함수 (부모함수의 this를 따라감)</li>
</ul>

#### this는 함수를 호출할때 정해짐 



<br><br><br>
<hr>
<br><br><br>



## 블록 스코프

(예시)
```Javascript

const x = true;
let y = false;

function a() {
  let a = 4;
  y = true;
  if (x) {
    let a = 3;
    for (let i = 0; i < 0;  i++){
      console.log(i);
    } // for 문에서 변수를 공유하고싶다면 부모선언에 빼기
    if (!y){
      kkk();
    }
  }
  //z(); // 에러 
}

a();
const z = (a, b) => { return a + b}; //TDZ / z선언
z(3, 5); // z 호출 / 8
```
<img src="https://user-images.githubusercontent.com/45233490/226826385-48724dbe-5240-4fb2-90de-9ae698ccd888.png" width="450"/><br>
* 선언지도 그리기 전에 호이스팅 되는 애들 있나 살펴보기 (functuib a)
* a함수에서 z를 호출할때 z가 선언전이기때문에 에러남
* 매개변수도 변수임




<br><br><br>
<hr>
<br><br><br>


## Promise 프로미스

* 내용이 실행은 되었지만 결과를 아직 반환하지 않은 객체 <br>
#### = 코드가 실행되었지만 결과값을 나중에 쓸수있음 !!! '_' b
```Javascript
const condition = true; // true면 resolve, false면 reject
const promise = new Promise((resolve, reject) => {
  if (condition) {
    resolve('성공');
  } else {
    reject('실패');
  }
});

// 딴짓딴짓~

// 이제 결괏값 사용할래!
promise
  .then((message) => {
    console.log(message); // 성공(resolve)한 경우 실행
  })
  .catch((error) => {
    console.error(error); // 실패(reject)한 경우 실행
  })
```

<br><br>

### Promise  ->   all 과 allSettled

```Javascript
const p1 = axios.get('서버주소1') // 성공
const p2 = axios.get('서버주소2') // 실패
const p3 = axios.get('서버주소3') // 성공

// all = 배열중 하나만 실패해도 에러로 넘어감
// 어디서어떻게 실패한건지 안 뜸 (성공한것까지 취소해서 다시 시도해야하는 번거로움)
// all에서 에러나도 catch, then에서 에러나도 catch
Promise.all([p1, p2, p3]).then((results) => {}).catch((error) => {});

// allSettled = 실패한 것만 필터링해서 다시 시도 / ★ allSettled만 쓰기!!!
// allSettled에서 에러나도 catch, then에서 에러나도 catch 
Promise.allSettled([p1, p2, p3]).then((results) => {}).catch((error) => {}).finally(() => {});


// finally = then이든 catch이든 쨋든 최종적으로 실행하는것

try {} catch (err) {}  finally {}
```
<br><br><br>



### Promise then은  async / await 로 가능!
- await = then / (async안에 await 있음)
- 변수 = await 프로미스;인 경우 프로미스가 resolve된 값이 변수에 저장
- ★ async/await는 resolve만 취급해서 try/catch 사용하여 reject문도 해줘야함
- 변수 await 값; 인 경우 그 값이 변수에 저장
- 오른쪽에서 왼쪽으로 읽어야함
<br><br>
await은 then(resolve)의 기능만 수행하고있어서 reject를 처리하려면 <br>
try{ await ~ }catch(error){ ~에러야~ } 가 필요함
<br>

```Javascript
// promise ~ then
const promise = new Promise(...)

promise.then((result) => ...)


// async ~ await
async function main(){
  try {
    const result = await promise;
    return result;
  } catch(error) {
    console.log(error);
  }
}

main().then((name) => ...)
```

<br><br>

### for await (변수 of 프로미스배열)
* promise 반복할때 사용 (for문이라고 생각하면됨)
* resolve된 프로미스가 변수에 담겨 나옴
* await을 사용하기 때문에 async 함수 안에서 해야함


```Javascript
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');

(async () => {
  for await (promise of [promise1, promise2]) {
    console.log(promise);
  }
})();
```


<br><br><br>
<hr>
<br><br><br>






## 비동기
* 한번 비동기는 영원한 비동기 (비동기 > 동기 바꾸기 X)
* 비동기는 코드순서와 실행순서와 다름 (동기코드는 위>아래, 왼>오)
* 비동기는 동시의 문제가 아님 (순서의 문제)
<br>

<strong>비동기는 동시의 문제가 아니라 순서의 문제 !!!</strong>

<br>

```
// setTimeout은 비동기
setTimeout(() => {
  console.log('a');
}, 0);
setTimeout(() => {
  console.log('b');
}, 1000);
setTimeout(() => {
  console.log('c');
}, 2000);
```
* 비동기에서는 우리가 그리던 호출스택, 선언지도만으로는 분석을 할수없음
  -> 그래서 '이벤트루프(E.L)' 등장!
<br><br>

<img src="https://user-images.githubusercontent.com/45233490/230810475-d3c52279-e939-49d5-a564-fc944234ecd1.png" width="450"/><br>


#### ▶  제로초의 비법으로 분석가능! *_* (추상적 개념)
* 백그라운드(BG)
  - 자바스크립트 X,  비동기들만의 세상
  - <u>비동기들이 동시에 돌아갈수있는 공간</u> (예: setTimeout 시간초를 동시에 셈)
  - setTimeout 타이머, promise, eventListner ... (비동기인애들이 한번씩 거쳐간다고 생각하면됨)
  - 백그라운드에 올라온 코드들은 태스크'큐'(= 매크로태스크큐, 마이크로태스크큐)를 거쳐야함
* 매크로태스크큐(M)
* 마이크로태스크큐(m)
  - promise ... (나머지는 매크로)
  - 매크로보다 우선순위 높음 ↑
<br>
=>위 분석을 하면 비동기코드를 동기처럼 보는것이 가능해짐






공부중,,,
