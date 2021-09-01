# 유틸리티 타입
: 이미 정의해 놓은 타입을 변환할 때 사용하기 좋음

-> 기존의 인터페이스, 제네릭 보다 유틸리티 타입을 쓰면 더 간결하게 타입을 정의할 수 있음

# 자주 사용하는 유틸리티 타입

## Pick
: 몇 개의 속성을 선택(union 연산자 이용)해서 정의

```TS
Pick<type이름, 'key이름'|'key이름'>
```

```TS
interface Hero {
  name: string;
  age: number;
  skill: string;
}
const human: Pick<Hero, 'name'|'age'> = { 
  name: 'yun',
  age: 22
}; 
```

## Partial
: 특정 타입의 모든 부분 집합을 만족하는 타입을 정의 (모든 속성을 optional 처리함)

```TS
Partial<type이름>
```

```TS
interface Address {
  email: string;
  address: string;
}

type MayHaveEmail = Partial<Address>;
const me: MayHaveEmail = {}; // 가능
const you: MayHaveEmail = { email: 'test@abc.com' }; // 가능
const all: MayHaveEmail = { email: 'capt@hero.com', address: 'Pangyo' }; // 가능
```

### Partial을 기존의 type 문법으로 구현해보기

```TS
interface UserProfile {
    username: string;
    email: string;
    profilePhotoUrl: string; 
}

// #1
type UserProfileUpdate = {
    username?: UserProfile['username'];
    email?: UserProfile['email'];
    profilePhotoUrl?: UserProfile['profilePhotoUrl'];
}

// #2 in operator 사용 (#1과 동일) -> 맵드 타입

/*
type UserProfileUpdate_ = {
    [p in 'username'|'email'|'profilePhotoUrl']?: UserProfile[p]
}
in operator를 사용하면 각 요소를 대입함
*/

type UserProfileKeys = keyof UserProfile

type UserProfileUpdate_ = {
    [p in UserProfileKeys]?: UserProfile[p]
}

// #3
type Partial<T> = {
    [p in keyof T]?: T[p];
}
```

## Omit
:  특정 타입에서 지정된 속성만 제거한 타입을 정의

```TS
Omit<type이름, 'key이름'|'key이름'>
```

```TS
interface AddressBook {
  name: string;
  phone: number;
  address: string;
  company: string;
}
const phoneBook: Omit<AddressBook, 'address'> = {
    //address를 뺀 나머지
  name: '재택근무',
  phone: 12342223333,
  company: '내 방'
}
const chingtao: Omit<AddressBook, 'address'|'company'> = {
    //address, company를 뺀 나머지
  name: '중국집',
  phone: 44455557777
}
```


