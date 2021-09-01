# 맵드 타입
: 기존에 정의되어 있는 타입을 새로운 타입으로 변환함. 

-> JS map() api 함수를 타입에 적용한 것과 같은 효과를 가짐


```TS
//예제
type Heroes = 'Hulk'|'Capt'|'Thor'

type HeroProfiles = { [K in Heroes]: number };
/*
위와 동일
type HeroProfiles = {
  Hulk: number;
  Thor: number;
  Capt: number;
}
*/
const heroInfo: HeroProfiles = {
  Hulk: 54,
  Thor: 1000,
  Capt: 33,
}
```


