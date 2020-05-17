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
      

# 이동욱 - 스프링 부트와 AWS로 혼자 구현하는 웹 서비스 개념 정리  
## 개발 환경
* Java 8 (JDK 1.8)
* Gradle 4.8 ~ Gradle 4.10.2
* IntelliJ Community  
* Visual Studio Code  
 * IntelliJ Community 버전의 경우, HTML, CSS, JS에 대한 지원이 없으므로, 이들에 대한 개발을 하기 위함이다.

### Chapter 1. 인텔리제이로 스프링 부트 시작하기  
많은 IT 회사에서 IntelliJ Ultimate를 공식 IDE로 채용한다.  
하지만 무료버전인 Community 버전에서도, Springboot를 개발하는데 크게 어려움이 없다. 이유는 다음과 같다.   
   
* 자바 개발에 대한 모든 기능 지원
* Maven, Gradle과 같은 빌드 도구 기능 지원
* 깃 & 깃허브와 같은 VCS(버전 관리 시스템) 기능 지원
* 스프링 부트의 경우 톰캣과 같은 별도의 외장 서버 없이 실행 가능  

프로젝트는 Gradle로 생성하며, 이 후 Gradle -> Spring boot project로 변경하여 개발한다.  

#### build.gradle
``` gradle
// 이 프로젝트의 의존성 관리를 위한 코드. - 1
buildscript { 
    ext {
        springBootVersion = '2.1.7.RELEASE'
    }
    repositories {
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}

// 위에 선언한 플러그인의 의존성들을 적용할 것이닞를 결정하는 코드 - 2
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'

group 'com.cafecoder.book'
version '1.0-SNAPSHOT'
sourceCompatibility = 1.8

// 각종 의존성들을 어떤 원격 저장소에서 받을지를 정한다. - 3
repositories {
    mavenCentral()
    jcenter()
}

// 의존성 코드 - 4
dependencies {
    compile('org.springframework.boot:spring-boot-starter-web')
    compile('org.projectlombok:lombok')
    compile('org.springframework.boot:spring-boot-starter-data-jpa')
    compile('com.h2database:h2')
    compile('org.springframework.boot:spring-boot-starter-mustache')

    testCompile('org.springframework.boot:spring-boot-starter-test')
}
```

