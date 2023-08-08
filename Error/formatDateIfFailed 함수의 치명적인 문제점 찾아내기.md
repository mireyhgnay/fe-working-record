# <div align="center">🚨 formatDetailFailed 함수의 치명적인 문제점 찾아내기</div>

<br>

## Info
공통 모듈 코어로 쓰이는 저장소에 있는 파일에서 치명적인 이슈 발견    
js파일에 `formatDateIfFailed` 이름의 함수가 있습니다.    
이 함수에는 치명적인 문제가 있는데 그걸 찾아내보기!!

<br>

## formatDateIfFailed() 함수
```JavaScript
formatDateIfFailed: function() {
        var date = new Date();
        var sDate = date.toJSON();
        var sTime = date.toTimeString();

        sDate = sDate.substring(0, 11);
        sTime = sTime.substring(0, 8) + '+09:00';

        return sDate + sTime;
}
```

<br>

## 코드 해석겸 콘솔 놀이
> Date() / toJSON() / toTimeString() / substring()
```JavaScript
let date = new Date();
console.log(date); // VM142:1 Fri Feb 03 2023 14:11:28 GMT+0900 (한국 표준시)

// 날짜,시간 전체 문자열로 반환 (JSON에서는 시간이 9시간 전으로나옴)
let sDate = date.toJSON();
console.log(sDate); // VM290:1 2023-02-03T05:11:28.131Z

// 시간만 문자열로 반환
let sTime = date.toTimeString();
console.log(sTime); // VM449:1 14:11:28 GMT+0900 (한국 표준시)

// sDate 인덱스 0 ~ 10 부분까지 문자열 반환
sDate = sDate.substring(0, 11);
'2023-02-03T' // 2023-02-03T05:11:28.131Z 여기서 0부터 11 전까지

// sTime 인덱스 0 ~ 7 부분까지 문자열 반환
sTime = sTime.substring(0, 8); // 14:11:28

sTime = sTime.substring(0, 8) + '+09:00'; // 14:11:28+09:00

console.log(sDate + sTime); // 2023-02-03T14:11:28+09:00
```
- Date() : 현재 날짜 시간 구하기
- toJSON()  : Date 객체의 문자열 표현을 반환합니다.
- toTimeString() : Date 객체의 **시간부분**의 toTimeString()메소드는 문자열로 변환하고 결과를 반환합니다.
- subString() : string 객체의 시작 인덱스로 부터 종료 인덱스 전 까지 문자열의 부분 문자열을 반환합니다.

<br>

## 알게 된 것
- toJSON() / toTimeString() / substring() 의 기능
- getMonth() 는 인덱스가 0 부터 시작되서 늘 +1 을 해주어야 맞는 달이 나온다

<br>

## 문제점
매일 시간에 맞춰 서비스 프로모션을 진행하는데 코드를 잘못 작성하여 시간 체크가 잘 되고있지 않았다.     
날짜와 시간을 직접 지정해서 toJSON 으로 변환해서 결과를 보면     
지정한 시간보다 9시간 전으로 찍혀 출력된다.

```JavaScript
let date = new Date(2023, 1, 4, 12).toJSON(); 
console.log(date); // '2023-02-04T03:00:00.000Z'
```

JSON 에서는 9시간 전으로 찍히니 별도로 toTimeString 으로 시간을 따로 구해서 합친 방법을 사용한 것 같다.

<br>

문제는! 다른 시간때는 괜찮을지 몰라도! 만약… 시간을 8시로 설정해본다면?
```JavaScript
let date = new Date(2023, 1, 4, 8).toJSON();
console.log(date); // '2023-02-03T23:00:00.000Z'
```
2월 4일 8시로 나오는 것이 아니라 9시간 전으로 돌아가니 하루 전으로 찍힌다.     
결과, 프로모션은 자정 딜인데 자정 넘어 9시 전까지 예정으로 간주하는 오류가 생긴 것이다.

![콘솔놀이](https://user-images.githubusercontent.com/111990266/216625677-6d7e9384-8181-4871-bd0d-bd748afe8bcf.png)

<br>

## 작업 내용
`formatDateIfFailed` 함수 수정 작업
- 함수가 한 서비스에서만 쓰이고 있는데 공통모듈에 존재하고 있음
- 함수를 제거하기엔 공통모듈에 존재하므로 전체서비스를 다 확인해봐야하는데 시간적으로 오래걸릴 뿐더러 무작정 지우다 다른 곳에서 에러가 날수 있음
    - 공통에서도 함수를 수정해두고, 적용해야 할 서비스 저장소에 별도로 추가하는 작업을 진행하기
- 이후 모든 서비스에서 쓰이지 않는 것 확실하게 확인하고 제거하기
- `formatDateIfFailed` 함수 수정하기

<br>

## 이슈 해결
> 이슈 해결 작업중...