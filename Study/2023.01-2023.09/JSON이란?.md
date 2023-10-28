# <div align="center">👩🏻‍💻 JSON란 무엇인가?</div>

<br>

## JSON (JavaScript Object Notation)

- Javascript에서 객체를 만들 때 사용하는 표현식을 의미한다.
- JSON은 데이터 포맷일 뿐이며 어떠한 통신 방법도, 프로그래밍 문법도 아닌 단순히 데이터를 표기하는 표현 방법일 뿐이다.

<br>

## JSON 특징

- 서버와 클라이언트 간의 교류에서 일반적으로 많이 사용됩니다.
- 자바스크립트의 객체 표기법과 아주 유사합니다.
- JSON 문서 형식은 자바스크립트의 객체 형식을 기반으로 만들어졌습니다.

**JSON의 기본 형태**

```json
{ key : value }
{ key1 : value1, key2: value2 }
{ key1 : { inKey : inValue }, key2 : [arr1, arr2 arr3] }
```

<br>

## JSON 문법

```json
{
  "employees": [
    {
      "name": "Hyerim",
      "lastName": "Yang"
    },
    {
      "name": "Someone",
      "lastName": "Park"
    }
  ]
}
```

- 자바스크립트와 마찬가지로 key와 value가 존재할 수 있고, key값이나 문자열은 항상 "" 쌍따옴표로 표기합니다.
- 객체, 배열 등의 표기를 사용할 수 있습니다.
- JSON형식에서는 null, number, string, array, object, boolean을 사용할 수 있습니다.

<br>

## JSON의 문제점

- AJAX는 단순히 데이터만이 아니라 자바스크립트도 전달할 수 있는데,
  그 말은 JSON데이터 인줄 알았는데 JavaScript 가 될 수도 있고 그게 실행될 수도 있는 것입니다.
  (= 데이터인 줄 알고 받았지만, 악성 스크립트가 될 수 있습니다.)

<br>

## JSON 형식을 JavaScript Object로 변환하는 방법

```javascript
// JSON 형식의 문자열
const jsonText = '{ "name": "Someone else", "lastName": "Kim" }';
const realObject = JSON.parse(jsonText); // JSON 텍스트를 javascript 객체로 변환
const jsonText2 = JSON.stringify(realObject); // 자바스크립트 객체를 json 텍스트로 변경

console.log(realObject);
console.log(jsonText2);
```
