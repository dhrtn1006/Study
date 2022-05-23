1. 윈도우에서는 인터넷에서 다운받고(Docker Desktop) 리눅스에서는 yum으로 install한다.

2. Docker를 실행시키고 원하는 OS의 이미지를 다운받는다.

    `docker pull centos:centos7`

3. 원하는 이미지를 확인하고 컨테이너를 생성한다.

    `docker images`

    `docker run -i -t  centos:centos7 /bin/bash`

4. 생성한 컨테이너를 확인하고 실행시킨후 접속한다.

    `docker ps -a`

    `docker start [container_id]`

    `docker attach [container_id]`

5. 컨테이너 나가기 및 종료

    실행 중 나가기 `ctrl + p` and `ctrl + q`

    종료 후 나가기 `ctrl + d`
​

도커는 가상 머신과 같이 독립된 운영체제를 만들어주는 역할을 하지만 실제 운영체제를 설치하지 않기 때문에 설치 용량이 적고 실행 속도 또한 빠르다. 예전에는 VM Ware와 같은 가상 머신을 설치하였으나 최근에는 Docker가 그 역할을 대신하고있다.

하지만 도커는 프로세스에 불과하므로 윈도우 운영체제에서 도커를 사용하여 리눅스 OS를 설치할 시 보안이슈등의 문제로 일부 명령어나 기능들이 제한될 수 있다.