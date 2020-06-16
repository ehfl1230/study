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
