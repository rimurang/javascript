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
3. anony 안에 a 있음 <br><br>


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







## 블록 스코프

(예시)
```Javascript

const x = true;
const y = false;

function a() {
  let a = 4;
  y = true;
  if (x) {
    let a = 3;
    for (let i = 0; i < 0;  i++){
      console.log(i);
    }
    if (!y){
      kkk();
    }
  }
  z(); // 에러 
}

a();
const z = () => {};
```
<img src="https://user-images.githubusercontent.com/45233490/226813734-12fe017a-9dc1-49ca-95cd-1a947e0770ed.png" width="450"/>
* 선언지도 그리기 전에 호이스팅 되는 애들 있나 살펴보기



# 공부중,,,
