[교재 학습] 스프링 부트와 AWS로 혼자 구현하는 웹서비스
=============

> ch02
- 테스트코드는 반드시 작성하자.
- 테스트코드로 먼저 확인후 프로젝트를 실행해 확인하기.
- gradle 4/5 버전별 lombok 및 jpa 설정이 상이하다(현업에서는 .4 버전을 많이 사용)

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
  
>  ch06 : AWS EC2 ( vCpu : 1 core / memory : 1GB / storage : 30GB )
1. 인스턴스 생성
2. 서버 스펙 설정(하드웨어 스펙 및 스토리지 용량)
3. 보안그룹 설정(방화벽)
   1. SSH 접속은 보안에 유의하자.(지정된 IP에서만 접속이 가능하도록)
4. 탄력적 IP 할당(인스턴스를 다시 시작하면 IP가 변경됨)
   1. 탄력적 IP는 생성하고 인스턴에서 바로 연결해야된다(비용 발생)
5. EC2 SSH 접속(MAC)
6. EC2 서버 환경셋팅
   1. java8 설치
   2. 타임존 변경(기본 서버시간은 미국시간)
   3. HostName 설정
  
>  ch07 : AWS RDS ( storage : 20GB )
1. MariaDB 인스턴스 생성(퍼블릭 엑세스 설)
2. 파라미터 그룹 생성 및 연결
   1. 타임존
   2. Character Set
   3. Max Connection
3. 로컬 -> RDS / EC2 -> RDS 접속 테스트

>  ch08 : 프로젝트 배포
1. ec2 git 설치 및 프로젝트 clone
2. maven or gradle 프로젝트 테스트 및 빌드
3. 배포 쉘스크립트 작성
   - nohup : 터미널이 종료될떄 애플리케이션은 계속 구동되도록 하기 위함
   - pgrep : 프로세스 id를 찾음
4. rds 연동(jdbc 설치 및 real-db 설정파일 생성)
   - db접속정보는 반드시 서버에서 관리가 되어야한다.(profile 분리를 통해)
5. 소셜로그인 url 변경

>  ch09 : Travis CI
1. Repository 활성화


   



  
 


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
