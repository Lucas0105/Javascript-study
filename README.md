# Javascript-study
- Airbnb Javascript Style Guide를 적용합니다.

# 자바스크립트 문법
- [선언식과 표현식](#선언식과-표현식)
- [Arrow Function](#arrow-function)
- [배열 메서드](#배열-메서드)
- [객체](#객체)
- [Json Object 변환](#json-object-변환)

# 웹
- [DOM](#dom)
- [Event](#event)
- [this](#this)


## 선언식과 표현식
- 선언식(호이스팅)
```
function add(num1, num2){
  return num1 + num2
}

add(2, 7)   # 9
```

- 표현식(권장)
```
const add = function (num1, num2){
  return num1 + num2
}
```

## Arrow Function
- function 키워드 생략
```
const add = (num1, num2) => {
  return num1 + num2
}
```

- 함수의 내용이 한 줄이라면 '{}' 와 'return' 생략
```
const greeting = (name) => `hello, ${name}`   // ` <= 이 문자를 백틱이라고 부름backtick
```

- 인자가 없다면 () or _ 로 표시가능
```
let noArgs = () => 'No args'
```

- object를 return 할 때(권장)
```
let returnObject = () => { return { key: 'value'} }
```

- return을 적지 않을 때
```
let returnObject = () => ( { key: 'value'} )
```


## 배열 메서드
- reverse
- push & pop
- unshift & shift (배열의 가장 앞에 요소를 추가 또는 제거)
- includes (특정 값이 존재하는지 참/거짓 반환)
```
const numbers = [1, 2, 3, 4, 5]

numbers.includes(1)   // true 반환
```

- indexOf (특정 값이 존재하는지 인덱스 반환)
```
numbers.indexOf(3)  // 2번 인덱스 반환

numbers.indexOf(100)  // 존재하지 않을 시 -1 반환 
```

- join (배열의 모든 요소를 구분자를 이용해 연결
```
numbers.oin()     // 기본 값은 쉼표로 연결 1, 2, 3, 4, 5
numbers.join('')  // 12345
numbers.join('-')  // 1-2-3-4-5

```

- callback 함수 : 어떤 함수의 내부에서 실행될 목적으로 인자로 넘겨받는 함수
- forEach
```
const numbers = [1, 2, 3]

numbers.forEach(function (number) {
  console.log(number)
})

numbers.forEach((number, index) => console.log(number))   // index 값은 선택적으로 인자로 사용 가능
```

- map (콜백 함수의 반환 값을 요소로하는 새로운 배열 반환)
```
const doubleFunc = function (number) {
  return number * 2
}

const doubleNumbers = numbers.map(doubleFunc)


const doubleNumbers = numbers.map((numbers) => number * 2)

```

- filter (콜백 함수의 참인 요소들만 모아서 새로운 배열 반환)
- reduce (콜백 함수의 반환 값들을 하나의 값에 누적 후 반환)
```
const sumValue = numbers.reduce((total, x) => total + x, 0) // 0은 초기 값으로 지정하지 않았을 시 배열의 첫번째 값으로 초기화 됨
// 만약 빈배열의 경우 초기 값을 지정하지 않으면 에러가 발생됨
```

- find (콜백 함수의 반환 값이 참이면 해당 첫번째 요소를 반환, 없으면 undefined 반환)
- some (요소 중 하나라도 판별 함수를 통과하면 참)
- every (모든 요소가 판별 함수를 통과하면 참)

## 객체
### 개요
- key는 문자열 타입만 가능
- key이름에 띄어쓰기가 있으면 따옴표로 묶어서 표현해야 함
- 객체 요소의 접근은 . 또는 []로 가능
- key이름에 띄어쓰기가 있으면 [] 접근만 가능

```
const me = {
  name: 'jack',
  'phoen number': '01012345678',
}
```

### 객체 관련 문법
- 속성명 축약(key와 할당하는 변수의 이름이 같으면 축약 가능)
```
const books = ['javascript', 'python']

const bookShop = {
  books: books,
}


const bookShop = {
  books,
}
```

- 메서드명 축약
```
const obj = {
  greeting: function () {
    console.log('Hi')
    }
  }
}

const obj = {
  greeting() {
    console.log('Hi')
    }
  }
}
```

- 계산된 속성(key의 이름을 표현식으로 이용하여 동적으로 생성 가능
```
const key = 'country'     // key의 값 변경 가능

const myObj = {
  [key]: 'value',
}
```

- 구조 분해 할당
```
const me = {
  name: 'jack',
  userId: 'jack123',
}

const { name } = me
const { userId } = me

// 여러개도 가능
const { name, userId } = me

```

## Json Object 변환
- JSON은 string 타입
- object는 object 타입

### Object to Json 
```
  const objToJSON = JSON.stringify(JSObject)
```

### Json to Object
```
  const JSONToObject = JSON.parse(objToJSON)
```

## DOM

### Document Object Model
- 논리 트리로 표현
- 문서를 표현, 저장, 조작하는 방법을 제공

### window
- 가장 최상위 객체(작성 시 생략 가능)

```
# 새 탭 열기
window.open()

# 인쇄 대화상자 표시
window.print()

# 경고 대화 상자 표시
window.alert()
```

### document
- 1. 선택, 2. 조작(생성, 추가, 삭제 등)

#### 선택 관련 메서드
- 일치하는 element 한 개 선택
```
  document.querySelector(selector)
```

- 일치하는 여러 element 선택
```
  document.querySelectorAll(selector)
```

#### 조작 관련 메서드
- 생성
```
  document.createElement(tagName)
```

- 입력
```
Element.innerText = ""
```

- 추가
```
Element.appendChild(another Element)
```

- 삭제 (제거된 Node 반환)
```
Element.removeChild(another Element)
```

- 속성조회 및 설정
```
  Element.getAttribute(attributName)
  
  Element.setAttribute(attributName, value)
```

- 토글(클래스에 해당 값이 존재한다면 제거하고 false, 존재하지 않으면 추가하고 true 반환)
```
element.classList.toggle(value)
```

## Event
- EventTarget.addEventListener(type, listener)
- 참조 사이트 (https://developer.mozilla.org/en-US/docs/Web/Events)

```
btn.addEventListener('click', function(event) {
  event.preventDefault()              # 현재 Event의 기본 동작을 중단(a 태그, form 태그)
  console.log(event.target)           # 이벤트의 대상
  console.log(event.target.value)     # 이벤트의 value 받아오기
  
})
```

### lodash
- 추가 기능을 제공하는 JS 유티리티 라이브러리
- 참조 사이트 (https://lodash.com/)
```
const numbers = _.sampleSize(_.range(1, 46), 6)
```

## this
- 함수 호출 방식에 따라 this 객체가 달라짐

- 전역객체는 모두 최상위 객체
```
cosnole.log(this)   # window
```

- 단순 호출 (window가 바인딩 됨)
```
const myFunc = function () {
  console.log(this)
}

myFunc()      # window
```

- Method (객체가 바인딩 됨)
```
const myObj = {
  data: 1,
  myFunc() {
    conosle.log(this)         # myObj
    console.log(this.data)    # 1
  }
}

myObj.myFunc()
```

- Nested (Function 키워드 => window 바인딩)

```
const myObj = {
  myFunc(){
    number.forEach( function (number) {
      console.log(this)     # window
    })
  }
}
```

- Nested (화살표 함수)
```
const myObj = {
  numbers: [1],
  myFunc(){
    number.forEach( (number) => {
      console.log(this)     # myObj
    })
  }
}
```

- addEventListener (fucnction 권장)
```
btn.addEventListener('click', function(event) {
  console.log(this)   # button 객체  => event.target
})
```

- addEventListener (화살표 함수)
```
btn.addEventListener('click', function(event) {
  console.log(this)   # window
})
```


## 기타
- HTML파일에서 실행하는 방법
```
<script>
  console.log('hello, javascript')
</script>
```

- js파일에 작성하고 HTML에 적용하는 방법

```
<script type='text/javascript' scr='hello.js'></script>
```
