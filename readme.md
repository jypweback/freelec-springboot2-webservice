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
- 기본적으로 브라우저에서 html을 읽어올때 head를 읽고 body를 읽는다. head가 다 불러지지 않으면 사용자 화면에서는
백지화면만 노출! 기본적으로 js 파일은 body 하단에/ css는 head에 구성하는것이 좋음(화면을 그려야 함으로)

> ch05 : OAuth 2.0 / Spring Security
- application-oauth는 보안에 중요함으로 git에 push 되지 않도록 gitignore에 추가하자
- .gitignore에 추가했음에도 commit 목록에 파일이 존재하면 캐시때문이다.
- 엔티티에 직렬화를 구현하는것에는 성능상 이슈가 발생될 수 있다.(연관관계의 다른 엔티티도 직렬화 대상에 포함이 되기 떄문)
- 반복되는 코드를 어노테이션 기반으로 리팩토링( HandlerMethodArgumentResolver 통해 반복로직을 줄일 수 있다.)
- 세션저장소 활용
  - 톰켓 세션
    - 일반적으로 세션은 내장톰캣의 메모리에 저장됨으로 서버가 재기동시에 세션이 날라감
    - WAS가 2개 이상일경우 세션 동기화를 위해 추가 설정이 필요함.
  - 데이터베이스 세션
    - 공용 세션을 하기 위해 가장 쉬운 방법
    - DB IO가 발생함으로 성능상 이슈가 발생할 수 있다.
    - 일반적으로 백오피스 시스템에서 많이 사용함.
  - Redis, Memcached
    - B2C 서비스에서 가장 많이 사용함.
    - 외부 메모리 서버가 필요하다.
- 스프링 시큐리티를 활성화할경우 테스트 환경에서도 정상적으로 실행할 수 있도록 가짜 사용자 셋팅을 해줘야함.(* MockMvc에서만 동작)
- @WebMvcTest( WebSecurityConfigurerAdapter, WebMvcConfigurer, @ControllerAdvice, @Controller)만 읽는다
  - @Repository,@Service,@Component는 스캔 대상이 아님.
  
>  ch06 : AWS EC2
-



```

@RequestParam
- API로 넘긴 파라메터를 가져올때 사용

@Transactional(readOnly = true)
- 트랜잭션 범위는 유지하되, 조회 속도를 개선할 수 있다.(등록,수정,삭제를 제외한 조회는 추가하는것을 추천)

@EnableWebSecurity
- Spring Security 설정들 활성

@WithMockUser(roles="USER")
- 테스트 메소드 실행시 가짜 사용자의 권한을 추

```



```
교재추천

DDD Start(최범균)
- 도메인 주도 개발 관련 추천서


```