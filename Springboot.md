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
  * Maven은 빌드 라이프 사이클의 중심 개념을 기반으로 한다. 이것은 

### 주로 사용되는 의존성 
* 'org.springframework.boot:spring-boot-starter-data-web'
* 'org.projectlombok:lombok'
* 'org.springframework.boot:spring-boot-starter-data-jpa'
* 'com.h2database:h2'
* 'org.springframework.boot:spring-boot-starter-mustache'
* 'org.springframework.boot:spring-boot-starter-test'

#### 1. org.springframework.boot:spring-boot-starter-data-web

