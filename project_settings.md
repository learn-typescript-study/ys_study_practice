# dependencies vs devDependencies
: NPM 지역 설치를 할 때는 해당 라이브러리가 배포용(dependencies)인지 개발용(devDependencies)인지 꼭 구분해주어야 함


- dependencies: 애플리케이션 로직에 직접적으로 관여함 -> 배포할때 포함됨

- devDependencies: 개발용으로만 관여함 -> 배포할 때 포함되지 않음

배포용 라이브러리는 `npm run build` 로 빌드 했을때 최종 애플리케이션 코드에 포함된다. 

설치 옵션에 `-D`를 주었다면 개발용 라이브러리로 다운된다. 개발할 때만 사용하고 배포에는 빠져도 좋은 라이브러리의 예시는 webpack(빌드 도구), eslint(코드 문법 검사) 등이 있다.

# tslint를 사용하지 않고 eslint를 쓰는 이유
: 성능 이슈가 있음. eslint에 tslint를 얹어서 가는 것으로 방향이 잡힘

---

# 외부 라이브러리 모듈화

## 외부 라이브러리 에러 처리
: npm으로 라이브러리를 다운받고 적용할때, 일부 외부 라이브러리에서는 type이 자동으로 처리되지 않아 직접 
- declaration file을 import하거나,
- `index.d.ts ` type 정의 모듈을 작성해야함
## Definitely Typed

타입 정의가 포함되지 않은 라이브러리를 `@types/라이브러리이름`으로 install을 도와주는 오픈소스

