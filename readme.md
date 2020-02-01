[교재 학습] 스프링 부트와 AWS로 혼자 구현하는 웹서비스
=============

> ch02
- 테스트코드는 반드시 작성하자.
- 테스트코드로 먼저 확인후 프로젝트를 실행해 확인하기.
- gradle 4/5 버전별 lombok 및 jpa 설정이 상이하다(현업에서는 .4 버전을 많이 사용

> ch03 : JPA
- Entity는 DB와 밀접한 클래스임으로 Request/Response DTO 클래스를 별도로 구성하자!
- @WebMvcTest의 경우 JPA 기능이 작동하지 않는다. JPA 기능까지 한번에 테스트할때는 @SpringBootTest,TestRestTemplate을 사용!
- Spring Data JPA
  - JPA 인터페이스를 구현한 추상화 모듈(JPA <- Hibernate <- Spring Data JPA)

> ch04 : View Template(머스테치)
- 


```

@RequestParam
- API로 넘긴 파라메터를 가져올때 사용

```



```
교재추천

DDD Start(최범균)
- 도메인 주도 개발 관련 추천서


```
