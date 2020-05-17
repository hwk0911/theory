# Spring-boot 2.x  
Spring-boot 2.x 정리  

Spring-boot 1.5.x 의 지원이 2019년 8월 1일 중단된다.  
따라서 2.x버전에 대한 학습을 위해 새로운 repository를 생성한다.  

### 지원 JDK  
* 1.5.x 에서는 JDK 6, 7을 지원했다. 하지만 **2.x 부터는, JDK 8사용이 강제된다.**
* JDK 8부터 지원하기 시작한, Interface의 Default method를 Spring framework 5.0에서 적극 사용했기 때문이다.  

### 빌드 도구   
* Gradle 4 이상
  * Gradle은 유연성과 성능에 중점을 둔 오픈 소스 빌드 자동화 도구이다.   
    Gradle은 Groovy, Kotilin DSL을 사용하여 작성된다.
    
  * 강점
    * 고도의 사용자 정의 기능 - Gradle은 가장 기본적인 방식으로 사용자가 정의하고, 확장 할 수 있는 방식으로 모델링 된다.
    * 빠름 - Gradle은 이전 실행의 출력을 재사용하고, 변경된 입력 만 처리하여 작업을 병렬로 실행한다.    
      따라서, 작업을 빠르게 완료할 수 있다.
    * 강력함 - Gradle은 많은 언어와 기술을 지원한다.
    
* Maven 3.2 이상
  * Maven은 Apache 라이선스로 배포되는 오픈 소스 소프트웨어다.   
    아파치 앤트의 대안으로 만들어졌다.
  * Maven은 빌드 라이프 사이클의 중심 개념을 기반으로 한다. 이것은, 특정 프로젝트를 빌드하고 배포하는 프로세스가 명확하게 정의되어 있다는 것을 의미한다.
    * 빌드 생명주기
      * validate - 프로젝트가 올바른지 확인하고 필요한 모든 정보를 사용할 수 있다.
      * compile - 프로젝트의 소스 코드를 컴파일
      * test - 적절한 단위 테스트 프레임 워크를 사용하여 컴파일 된 소스 코드를 테스트한다. 이러한 테스트는 코드를 패키지하거나, 배포 할 필요가 없다.
      * package - 컴파일 된 코드를 가져와, JAR와 같은 배포 가능한 형식으로 패키지한다.
      * verify - 품질 기준을 충족시키기 위해 통합 테스트 결과에 대한 점검을 수행한다.
      * install - 다른 프로젝트에서 로컬로 종속성으로 사용하기 위해 패키지를 로컬 저장소에 설치한다.
      * deploy - 빌드 환경에서 완료되면 다른 개발자 및 프로젝트와 공유하기 위해 최종 패키지를 원격 저장소에 복사한다.
      
     이 수명주기 단계는 default수명주기를 완료하기 위해 순차적으로 실행된다.   
     위의 라이프 사이클 단계에서 기본 라이프 사이클을 사용하면, Maven은 먼저 프로젝트를 검증 한 다음,  
     소스를 컴파일하고, 테스트를 대상으로 소스를 실행하고, 바이너리(ex: jar)를 패키징하고,   
     통합 테스트를 실행한다. 확인 된 패키지를 로컬 저장소에 설치 한 후 설치된 패키지를 원격 저장소에 배치한다.   
      

### 주로 사용되는 의존성 
* 'org.springframework.boot:spring-boot-starter-data-web'
* 'org.projectlombok:lombok'
* 'org.springframework.boot:spring-boot-starter-data-jpa'
* 'com.h2database:h2'
* 'org.springframework.boot:spring-boot-starter-mustache'
* 'org.springframework.boot:spring-boot-starter-test'

#### 1. org.springframework.boot:spring-boot-starter-data-web

