https://velopert.com/3613

<h3>JSX</h3>

* 태그는 반드시 닫혀야 함.
* 최종적으로 무조건 하나의 엘리먼트로 감싸져 있어야 함.
* 단순히 감싸기 위해 \<div\>를 사용해야 할때는 \<Fragment\>라는 것을 사용하도록한다.
* 형식
    * const 상수 선언
    * let 변수 선언 (scope가 함수 단위)
    * var 변수 선언 (scope가 블록 단위) => 이건 이제 안쓴다고 본다.
* 조건부 렌더링 할때는 삼항을 주로 사용
* 복잡하면 밖에서 로직 작성하는 것이 좋음
* (() => {})() 화살표 함수. this, arguments, super 개념이 없는 익명 함수
* style 
    * const style = {style1:style, style2:style};
    * \<div style={style}\>\</div\>
    * 클래스 적용시에는 \<div className="App"\>
* 주석 
    * {/* ... */}

<h3>컴포넌트</h3>

  * 클래스형 컴포넌트
  <pre>
  class MyName extends Component {  
    render() {
        return ();
    }
  }
  </pre>
* 함수형 컴포넌트
<pre>
const MyName = ({name}) => { 
    return ();
};
</pre>
차이는 라이프 사이클이 없어 메모리 자원을 덜 사용한다는 것. 미세해서 큰 차이는 없다.


<h3>Props와 Statement</h3>
<h4>props</h4>

* 부모 컴포넌트가 자식 컴포넌트에게 주는 값
* static defaultProps = {}

<h4>state</h4>

* 동적인 데이터를 다룰 때 사용한다.
<pre>
state = {
}
or
constructor(props) {  
    super(props);  
    this.statue = {  
    }
}
# 둘다 사용한다면 class field가 먼저 실행된다.
</pre>

* 메소드 작성할 때는 
<pre>
handleIncrease = () => {
    this.setState({
        key:value;
});
}
</pre>
와 같이 해준다. 

* handleIncreate() 와 같이 작성하면 this와의 연결이 끊겨버리기 때문에 위와 같이 작성한다.
* setState 무조건 해야지 리렌더링 됨.

<h3>비구조화 할당</h3>

<h3>라이프사이클</h3>
<h5>컴포넌트 초기 생성</h5>
<h6>
constructor</h6>
<pre>
constructor(props) {
    super(props);
}
</pre>
<h6>componentWillMount</h6>
화면에 나가기 직전에 호출되는 api
=> 16.3 deprecated 됨
<h6>componentDidMount</h6>

* 화면에 나타나게 되었을 때 호출됨.
* axios, fetch 등을 통해서 ajax 요청을 하거나 dom 속성 읽거나 변경할 때 사용

<h5>컴포넌트 업데이트</h5>
<h6>componentWillReceiveProps</h6>

* api는 컴포넌트가 새로운 props 받게 되었을 때 호출됨.
* state가 props에 따라 변해야 하는 로직을 작성
-> deprecated됨.

<h6>static getDerivedStateFromProps()</h6>

* 16.3 이후 만들어진 라이프사이클
* props로 받아온 값을 state로 동기화하는 작업

<h6>shouldComponentUpdate</h6>

* 컴포넌트 최적화 작업에 유용하게 사용됨
* 기본적으로 true를 반환하며 false를 반환하면 해당 조건에는 render함수를 호출하지 않음

<h6>componentWillUpdate</h6>

* shouldComponentUpdate에서 true를 반환했을 때만 호출됨.
* 애니메이션 효과 초기화 or 이벤트 리스너 없애는 작업
* 16.3 이후 deprecate됨. 기존 기능은 getSnapshotBeforeUpdate로 대체 가능

<h6>getSnapshotBeforeUpdate()</h6>

* 발생시점?
    * render()
    * getSnapshotBeforeUpdate()
    * dom 변화 발생
    * componentDidUpdate
    
<h6>componentDidUpdate</h6>

* render() 호출하고 난 다음 발생
* this.props와 this.state가 바뀌어 있음.
* 파라미터를 통해 precProps와 prevState 조회 가능
* getSanpshotBeforeUpdate에서 반환한 snapshot값을 세번째로 받아온다.

<h5>컴포넌트 제거</h5>
<h6>componentWillUnmount</h6>

* 이벤트 제거
* setTimeout제거
* 외부라이브러리 인스턴스 제어

<h5>컴포넌트 에러 발생</h5>
componentDidCatch(error, info) {
    this.setState({
        error: true
})
}
* 자기 자신의 render 함수에서 에러가 발생하는건 못잡고, 자식 컴포넌트 내부에서 발생하는 에러는 잡을 수 있다.

<h3>부모 컴포넌트에게 정보 전달하기</h3>
* 부모 컴포넌트에서 메소드를 만들고
* 이를 하위 메소드한테 전달해서 하위 메소드에서 변경하상이 있으면 props로 받은 함수 호출하여 다시 부모한테 전달한다.
