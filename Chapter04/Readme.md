### 도커 컴포즈
다중 컨테이너 환경의 도커 애플리케이션을 정의하고 실행을 위한 도구이며 YAML(YML) 파일을 사용해서 여러 개의 컨테이너를 한 번에 관리 가능한 기술이다.

### 도커 컴포즈를 사용하는 이유
웹 애플리케이션을 수행하려면 웹 서버 컨테이너와 데이터베이스 컨테이너를 매번 CLI로 생성해야하는데 도커 컴포즈를 사용하면 여러 개의 컨테이너를 한 번에 실행하고 관리가 가능하기 떄문에 편리성이 증가한다.

### 도커 컴포즈 설치
~~~
sudo curl -L "https://github.com/docker/compose/releases/download/{도커 컴포즈 버전}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
~~~
리눅스에서는 위 명령어로 도커 컴포즈를 설치 후
~~~
sudo chmod +x /usr/local/bin/docker-compose
~~~
위 명령어로 도커 컴포즈가 실행 가능하도록 권한을 부여해야한다.

윈도우와 맥에서는 도커 설치 시 도커 컴포즈도 같이 설치되기 떄문에 따로 설치할 필요가 없다. 
~~~
docker-compose -v
~~~
위 명령어를 통해서 버전을 확인할 수 있다.

### 도커 컴포즈 YAML(YML) 작성
YAML(YML) 파일은 탭이 인식되지 않아서 하위 항목을 2칸씩 띄워서 구분한다.
|   명령어    | 의미                                                        |
| :---------: | :---------------------------------------------------------- |
|   version   | 도커 컴포즈의 스키마 버전 되도록 최근의 버전을 사용         |
|   service   | 실행 서비스 목록을 정의                                     |
|    image    | 서비스에서 사용할 도커 이미지                               |
|    build    | 이미지 대신 사용할 빌드 옵션                                |
|   context   | 빌드 명령을 실행할 디렉토리 경로                            |
| dockerfile  | 도커 이미지를 빌드하는데 사용할 도커파일의 위치             |
|   command   | 커맨드 변경이 가능하며 명령어를 통해 실행 가능              |
|    port     | 노출시킬 포트를 설정하며 -를 통해서 여러개의 포트 노출 가능 |
| working_dir | 작업 디렉토리를 지정                                        |
|   volume    | 마운트할 볼륨을 지정하며 상대경로로도 입력가능              |
|    links    | 통신할 다른 컨테이너를 정의                                 |

### 도커 컴포즈 자주 사용되는 커맨드
~~~
# 도커 컴포즈 컨테이너들을 백그라운드로 띄우기
$ docker-compose up -d
 
# 도커 컴포즈 컨테이너들을 포어그라운드로 띄우기
$ docker-compose up
 
# 도커 컴포즈 컨테이너들을 내리기
$ docker-compose down
 
# 도커 컴포즈 컨테이너들을 다시 시작하기
$ docker-compose restart
 
# 도커 컴포즈 컨테이너들의 로그를 계속해서 읽기
$ docker-compose logs -f
 
# 도커 컴포즈 컨테이너들의 상태 확인
$ docker-compose ps
 
# 도커 컴포즈 설정을 확인
# 주로 -f 옵션으로 여러 개의 설정 파일을 사용할 때, 최종적으로 어떻게 설정이 적용되는지 확인해볼 때 유용합니다.
$ docker-compose config
 
# 다른 경로에 있는 도커 컴포즈 파일 사용
# 도커 컴포즈로 다른 이름이나 경로의 파일을 Docker Compose 설정 파일로 사용하고 싶다면 -f 옵션으로 명시를 해줍니다.
$ docker-compose -f /app/docker-compose.yml up

# 여러개의 도커 컴포즈 설정 파일을 사용할 수 있습니다. 이 때는 나중에 나오는 설정이 앞에 나오는 설정보다 우선하게 됩니다.
$ docker-compose -f docker-compose.yml -f docker-compose-test.yml up
~~~

<br>
<br>
<br>

### 참조 블로그
[도커 컴포즈를 활용하여 완벽한 개발 환경 구성하기](https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose#docker-compose.yml-%ED%8C%8C%EC%9D%BC)

[도커 컴포즈 가이드라인](https://danawalab.github.io/docker/2021/01/13/docker-compose-guideline.html)