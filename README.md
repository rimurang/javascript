## React.js (기초)

### [공부 자료]
- [리액트 무료 강좌(웹게임)](https://www.youtube.com/watch?v=aYwSrzeyUOk&list=PLcqDmjxt30RtqbStQqk-eYMK8N-1SYIFn)
- [react-webgame - 저장소](https://github.com/ZeroCho/react-webgame/tree/react18)

### [일정]
- 4월 4주차(4/24~30) : 리액트 무료 강좌 1-1 ~ 1-10
- 5월 1주차(5/1~7) : 리액트 무료 강좌 2-1 ~ 2-11
- 5월 2주차(5/8~14) : 리액트 무료 강좌 3-1 ~ 3-13
- 5월 3주차(5/15~21) : 리액트 무료 강좌 4-1 ~ 4-5
- 5월 4주차(5/22~28) : 리액트 무료 강좌 5-1 ~ 5-7
- 5월 5주차 - 6월 1주차(5/29~6/4) : 리액트 무료 강좌 6-1 ~ 6-6
- 6월 2주차(6/5~11) : 리액트 무료 강좌 7-1 ~ 7-5

### [유의 사항]
- Node.js 16버전 이상 사용해야 합니다.(18 LTS 버전도 괜찮음)



<br><br><br><br>
## 리액트 

#### = 싱글페이지 애플리케이션

데이터와 화면의 일치문제 해결 (ex.닉네임 바꿨는데 다른 화면에서는 안바뀌어있는 경우,,)
리액트.. 한국에서 대세.. 대세 따라가기

* 새로운 존재가 아닌 리액트도 결국 자바스크립트일뿐이고 이로 html와 css를 만들어내는것
 = 결과물은 html, css, javascript 임
 
* 리액트는 데이터중심으로 움직임
 

<br>

#### ▶ 리액트엔 크게 두가지 방식이 있다!

!!!! 클래스와 함수 !!!!
- 근데 클래스는 요즘 거의 안쓰임..(99%).. 그래도 알아두기(예전 작업자에의해 사용되었을지도)
- 함수(화살표함수)를 잘 익혀두자~

```Javascript
// 클래스
class LikeButton extends React.Component {
 ~~
}

// 함수
const LikeButton = () => {};
function LikeButton() {};
```
<br>

#### ▶ 컴포넌트

데이터와 화면을 하나로 묶어놓은 덩어리 (데이터 중심)

```Javascript
// 클래스
class LikeButton extends React.Component {
 constructor(props){
  super(props);
  this.state = {Liked. false}; // 데이터 (화면의 바뀌는 부분은 state로..)
 }
 render() {
  if (this.state.liked) {
   return 'You Liked this';
  }
 }
 
 return React.createElement('button', {onClick: () => this.setState({liked: true})}, 'Like'); // 화면
 ~~
}
```

<br>

#### ⚠️ BUT,, 자바스크립트로만 하다보니 가독성이 안좋음
<strong>JSX</strong>


