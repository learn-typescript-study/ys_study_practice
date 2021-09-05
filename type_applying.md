# 화살표 함수에 type 적용하기

```TS
//기존과 동일, 괄호 치기만 주의하기

let sum = (a:number,b:number): number => {
    return a+b; 
}
```

# 정해져 있는 문자열을 넘기고 받을 때 enum 사용하기
: status 를 주고받을 때 문자열을 직접 주고 받기보다는, enum으로 정의해두기
```TS
enum CovidStatus {
  Confirmed = 'confirmed',
  Recovered = 'recovered',
  Deaths = 'deaths'
}

```

# DOM 함수 타입 오류 해결하기

-> missing Following Properties 오류 해결하기

    : api 파악하고 `as` 키워드 활용하기

-> 타입 호환이 되지 않는 경우, 호환할 수 있도록 타입 단언을 이용한다
