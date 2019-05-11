[초보를 위한 도커 안내서 - 도커란 무엇인가?](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html)  
[초보를 위한 도커 안내서 - 설치하고 컨테이너 실행하기](https://subicura.com/2017/01/19/docker-guide-for-beginners-2.html)  
[초보를 위한 도커 안내서 - 이미지 만들고 배포하기](https://subicura.com/2017/02/10/docker-guide-for-beginners-create-image-and-deploy.html)  

# 도커(Docker) 란?
**컨테이너 기반의 오픈소스 가상화 플랫폼**  
다양한 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 관리를 단순하게 해준다.
백엔드 프로그램, 데이터베이스 서버, 메시지 큐등 어떤 프로그램도 컨테이너로 추상화할 수 있고, 어디서든 실행할 수 있음.
  
기존의 가상화 방식은 주로 **OS를 가상화** 하는 것 이었음. 하지만, 이 방식은 무겁고 느려서 운영환경에서 사용할 수 
없었음. 이것을 개선하여 **전체 OS를 가상화하는 방식이 아니라, 호스트OS와 다른부분만 가상화하는** 방식이 등장. 이것이
도커의 기반이라 할 수 있음.
![IMAGE](https://subicura.com/assets/article_images/2017-01-19-docker-guide-for-beginners-1/vm-vs-docker.png)
오른쪽의 **Docker Engine**이 바로 Host OS와 컨테이너에서 필요로하는 OS의 다른부분만 가상화한 것.

## 이미지
![이미지](https://subicura.com/assets/article_images/2017-01-19-docker-guide-for-beginners-1/docker-image.png)
이미지는 컨테이너 실행에 필요한 파일과 설정값등을 포함하고 있는 것. 상태를 가지지 않고 변하지 않는다.
- ubuntu 이미지는 ubuntu를 실행하기 위한 모든 파일을 가지고 있음.
- MySQL 이미지는 debian을 기반으로 MySQL을 실행하는데 필요한 파일과 실행 명령어, 포트정보등을 가지고있음.
- Gitlab 이미지는 centos를 기반으로 ruby, go, database, redis, gitlab source, nginx등을 가지고 있음.
  
종합하자면, 이미지는 컨테이너를 실행하기 위한 모~든 정보를 다 가지고 있기 때문에 더 이상 의존성 파일을 컴파일하고
이것저것 설치할 필요가 없음. 새로운 서버가 추가되면 미리 만들어 놓은 이미지를 다운받고 컨테이너를 생성만 하면 됨!!
한 서버에 여러 컨테이너를 실행할 수 있음!

## 컨테이너
컨테이너는 이미지를 실행하고있는 instance 라고 볼 수 있음. OS 관점에서 보자면, 하나의 프로세스 임! 해당 프로세스
에서 Target OS인 척 하기위해, Host OS의 다른부분의 정보를 추가적으로 가지고 있는 상태! 당연히 상태를 가지고,
추가되거나 변하는 값은 고스란히 저장됨. 당연히 같은 이미지에서 여러개의 컨테이너를 생성할 수 있음.




## nginx 란?
[참고사이트](https://medium.com/sjk5766/%EB%84%8C-%EB%AD%90%EB%8B%88-nginx-9a8cae25e964)  
nginx는 서버 SW의 일종임. Node.js, Django, Spring Boot 등으로 제작한 응용프로그램이 OSI 7계층 중 Application layer에서 동작한다면,
nginx와 같은 서버 SW는 그아래에서 동작한다. 다수의 클라이언트와 HTTP 통신을 하게 된다는 것!  
nginx는 apache 서버 SW와 많이 비교된다.

### Apache
Apache는 Multi-Process-Module을 사용한다. 크게 두가지 방식이 있는데, 멀티 프로세스방식과 멀티 프로세스-스레드 방식이다.  
멀티 프로세스방식: client 에게 process 하나를 할당하여 response한다
멀티 프로세스-스레드 방식: client 에게 process를 할당하고 숫자가 많아지면 process에서 스레드를 생성하여 할당한다.  

### NGINX는?
비동기 방식. 싱글스레드로 Event-driven방식을 통해 병렬 처리를 한다. 비동기 Event-driven 방식으로 병렬처리를 한다는 말은 다음과 같다.
앞선 처리를 하다가, socket I/O, Network 등등의 cpu가 대기해야하는 작업이 시작될땐 콜백함수를 등록해놓고 바로 다음 client의 처리를 시작한다는 것.
이것은 병렬처리에 있어, 자바는 멀티스레드로 대응하는 반면에 Node.js는 비동기 evnet-driven방식의 대응을 하는 양상에서, Node.js의 병렬처리 방식과 같다고 할 수 있다.
