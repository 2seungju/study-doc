TOMCAT
======

개요
톰캣이란 아파치 소프트웨어 재단의 Web Application Server(WAS)로서,웹 서버와 웹 컨테이너의 결합으로 동적인 역할을 수행할 수 있는 서버를 말한다.

![tomcat](/image/tomcat_overview.png)

###Web Server(Apache) VS WAS(Tomcat)
둘의 가장 핵심적인 차이는 어떤 타입(동적, 정적)의 컨텐츠를 제공하냐는 것이다.  

|`장점`                    |`단점`                |
|-------------------------|-------------------|
|아파치 처리 속도가 빠르다.    |정적인 데이터만 처리가능|  
|톰캣 데이터 흐름이 유동적(동적)| 느린 처리 속도       |

Web Server와 WAS를 같이 사용하는 이유  
WAS안에도 Web Server가 포함되어 있는데 굳이 왜..?  
=> 
* WAS가 해야할 일의 부담을 줄이기 위해서  
WAS 앞에 웹 서버를 배치한 후, 웹 서버에서 정적 컨텐츠를 처리하도록하고, WAS는 애플리케이션의 로직만 수행하도록 기능을 분리해서 효율적
으로 데이터를 처리

* 보안  
클라이언트와 연결하는 포트가 직접 WAS에 연결되어 있다면 중요 설정 파일들이 노출될 수도 있다는 위험이 있을 수 있기 때문에 외부에 노출시
키지 않도록 하기 위해  
웹 서버와 WAS의 포트가 다르기 때문에 WAS에 들어오는 포트에는 방화벽을 쳐서 보안을 강화할 수도 있다.

![tomcat_dir](/image/tomcat_dir.png)  

톰캣 디렉토리

|이름|설명|
|---|---|
|bin| startup, shutdown, 기타 스크립트가 존재한다. sh 파일(유닉스 시스템)과 bat 파일(윈도우 시스템)은 기능적으로 동일하다.|
|conf| 설정 파일과 DTD와 연관된 파일이 존재한다. 가장 중요한 파일인 server.xml이 있으며 이 파일은 컨테이너의 주요 설정 파일이다.|
|logs| 기본적으로 이 디렉토리에 로그 파일이 생성된다.|
|webapps| 기본 webapps가 위치하는 디렉토리이다.|
|lib| classpath에 추가되는 리소스가 위치한 디렉토리이다.|
|work| Jsp 파일을 서블릿 형태로 변환한 java 파일과 class 파일이 저장되는 디렉토리이다.|
|temp| JVM에 사용되는 임시 디렉토리이다.|

bin  
![tomcat_bin](/image/tomcat_bin.png)

|이름|설명|
|---|---|
|bootstrap.jar| Tomcat 서버가 구동될 때 사용되는 main() 메소드가 포함되어 있으며 클래스 로더가 클래스를 구현하는데에 필수적이다.|
|tomcat-juil.jar| 로깅을 구현하는 java.util.logging API를 포함하고 있는 클래스이다.|
|common-daemon.jar| Apache Commons Daemon 프로젝트에 필요한 클래스이다.|
|Catalina.sh| 파일에 의해 빌드되지 않으며 bootstrap.jar 파일에 의해 참조된다.|
|catalina.sh| CATALINA 서버의 제어 스크립트이다.|
|ciphers.sh| 지정된 알고리즘을 사용하는 다이제스트 암호를 설정하는 스크립트이다.|
|configtest.sh| CATALINA 서버의 설정 스크립트이다.|
|daemon.sh| Common Daemon에 사용되는 스크립트이다.|
|digest.sh| 지정된 알고리즘을 사용하는 다이제스트 암호를 설정하는 스크립트이다.|
|makebase.sh| Tomcat 실행에 필요한 분산 디렉토리 구조를 생성하는 스크립트이다.|
|setclasspath.sh| JAVA_HOME 또는 JRE_HOME이 세팅되지 않았을 경우 세팅한다.|
|shutdown.sh| CATALINA 서버를 중지하는 스크립트이다.|
|startup.sh| CATALINA 서버를 시작하는 스크립트이다.|
|tool-wrapper.sh| 커맨드 라인 도구에서 사용되는 Wrapper 스크립트이다.|
|version.sh| Tomcat의 정보를 표시해주는 스크립트이다.|

catalina.sh에는 JAVA_OPTS, CATALINA_OPTS 두 가지 실행 옵션을 지정할 수 있는데,  
JAVA_OPTS : start, stop, run 명령을 실행하는 java 프로세스에 모두 쓰임  
CATALINA_OPTS : start와 run 명령을 실행하는 java 프로세스에만 쓰임  
이러한 환경변수는 catalina.sh를 직접 고쳐서 수정하기 보다는 별도의 스크립트에서 지정하는 것이 바람직하다. 톰캣 버전을 업데이트할 때 catalina.sh를 덮어쓸 수
도 있기 때문  

톰캣의 메뉴얼에는 이러한 변수를 setenv.sh에 설정하는 것을 권장하고 있다.
![setenv](/image/setenv.png)


