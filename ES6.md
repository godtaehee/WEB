# JSON 객체

데이터를 저장하고 전송하기 위한 데이터포멧 ( JavaScript Object Notation )

JS의 Object에서는 키에해당하는것은 쌍따옴표가 없어도 되지만 JSON은 키든 값이든 모두 쌍따옴표를 써줘야한다

```jsx
var data = {
            "employee": [
                {"First": "태희", "Last" : "김"},
                {"First": "수현", "Last" : "강"},
                {"First": "선준", "Last" : "고"}
            ]
        }

JSON.stringify

JSON 데이터를 String으로 변환

JSON.parse

JSON 데이터의 형식을 그대로 갖춘 String을 매개변수로 넣으면 그것을 Object로 반환해줌
```

# Window 객체

```jsx
alert() : alert창 보여줌
confirm() : 확인 취소 창
prompt() : 값을 받는창, 아무것도 안하면 "", 취소하면 null
window.open(주소) : 주소를 출력해줌
window.print() : 현재 보는 페이지를 프린트해줌
setTimeout(함수, 밀리세컨드 1000이 1초); 시간 뒤에 함수를 실행
setInterval(함수, 시간); 시간 마다 함수를 실행
setInterval안에 clearInterval을 해줘야하는데 clearInterval(setInterval을 했던 변수이름)
웹소캣: 웹의 기본동작과정은 클라이언트가 request를 해야 서버가 response를 해주는 방식인데 웹소캣은
클라이언트의 리퀘스트가 없어도 response를 해줄수 있다.
주식차트 프로그램에서 1초마다 서버로부터 주식의 정보를 계속 받아와서 클라이언트에 보여주는 방식이 옛날방식인데
이게 근데 사용자가 조금이면 모르겠는데 1000명 10000명이면 그 많은사람들한테 1초에 한번씩 계속 보내면 
서버에 부하가 일어난다 예를들어 삼성전자의 주식값이 8만원인데 1초후의 삼성전자 값도 8만원이면 서버는 클라
이언트에게 이 정보를 보내지 않는다 만약근데 1초후에 8만1천원으로 올르면 그때서야 response를 보낸다.

```

# 크롬 개발자 도구

```jsx
console.log
console.info 정보
console.warn 경고
console.error 에러
console.table(객체); -> 객체를 테이블형식으로 볼수있음 정렬해서 볼수도있음

console.time()
/ some code /
console.timeEnd(); : time ~ timeEnd사이에있는 코드의 실행속도, 퍼포먼스능력을 확인한다

console.log("%csdfasdfsaasdf", "color:yellow;background-color:yellow;padding:5px;"); -> %c 뒤에있는 문자를 노란색으로 스타일링 하겠다.

XHR(XML HTTP REQUEST) : JSON 객체들 볼수있다.

```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a467bd43-5610-4339-bc18-4c5ba74733a5/_2021-04-10__9.55.11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a467bd43-5610-4339-bc18-4c5ba74733a5/_2021-04-10__9.55.11.png)

Default levels에서 보여주고싶은 메세지만 선택해서 볼수있음

Filter에서 원하는것만 볼수있음

# this 키워드

```jsx
오브젝트 안에 this는 오브젝트를 가리키며 예를들어
let person = {
	fullName : this.firstName + this.lastName이렇게 ㄱ ㄱ
};

함수 안에 this는 window를 의미함

<button type="button" onclick="this.style.backgroundColor='red'"> 이때 this는 버튼
html태그안에서 this를 쓰면 html태그(엘리먼트)를 가리킴 

select의 onchange는 select박스의 option이 바뀔때마다 실행되는 함수
```

# Scope

```jsx
변수에 대한 접근성을 의미

함수 안에 변수는 함수안에서만 접근가능 var든, let이든, const든 상관없 이것을 local scope라고 함

브라우저가 html파일을 열고 스크립트쪽을 먼저 해석한다

function 키워드는 먼저 해석을한다. 하지만 함수를 변수에 담아버리면 30번째 라인에 올때 비로소 해석한다.

이런것을 자바스크립트 엔진이 자바스크립트 코드를 해석하는 순서이다.
/
```

# DefaultFunction Parameter

```jsx
ES6 - ECMAScript 6버전 에서 있는 기능이다.
function say(message="매개변수가 넘어오지 않았습니다."){
				console.log(message);
}
```

# Rest Parameter

```jsx
function sum(...args) {

args.forEach(function(x(값), index(인덱스)) {
total+= x;
}
};
```

# Arrow Function

```jsx
코드가 만약 한줄이면 return도 생략가능 중괄호도 생략가능
파라미터가 한개이면 중괄호 자체도 또 생략가능

```

# Template Literals

```jsx
`${변수}`
```

# Object Literal Syntax Extension

```jsx
let go = "name";
        let obj = {
            [go]:"김태희"
        }
```

# Spread Operator

```jsx
let arr = [1,2,3];
let arr2 = [4,5,6];
let newarr = [1,2,3,...arr2];
let newarrr = [1,...arr2,2,3];
```

# Object Destructuring

```jsx
오브젝트의 키값을 기반으로 변수명을 바로 받아올수있다.

const getPerson = function (){
            return {
                first:"김태희",
                second:"김도영"
            }
        }

        var {first, second} = getPerson();
        console.log(first);
        console.log(second);

```

# Array Destructuring

```jsx
function getArr() {
	return [1,2,3];
let [x,y,z] = getArr();
```

# Mock 서버

```jsx
Postman이라는걸 설치한다
목서버에 가짜서버를 만들어서 프론트엔드를 테스트할때도 유용하지만
반대로 서버개발자가 서버프로그램에 개발해놓은 API가 클라이언트쪽에서 정상적으로 호출되는지도 유용하게 사용할수있다.

```

# Promise

```jsx
비동기 통신을위한
예를들어 다음 코드에서
var x = 1;
//서버 호출해서 데이터를 받아오는 함수
// y = callServerData();
var z = x + y;
서버데이터를 요청했는데 요청에대한 응답이 도착하기도 전에 다음 코드를 실행시켜버릴수있다.
그렇게되면 y에 아무런 값도 안저장되서 마지막 줄에서 에러가 뜰수있다.
이때 서버에서 데이터가 올때까지 기다릴게라고 약속하는 함수가 Promise이다.
 그데이터가 올때까지 다음 코드 실행안하겠다. 라고하는것
//axios라고 있다.

```
