1. nssm 홈페이지에서 release 버전의 nssm을 다운로드한다.

    `https://nssm.cc/download`

2. 다운로드 받은 zip 파일을 원하는 경로(c드라이브 내부)에 두고 압축을 해제한다.

3. cmd로 64비트 폴더 내부의 nssm을 실행한다.

    `nssm install 서비스명`

4. path에 실행경로를 등록하고 완료한다.

5. nginx의 경우 nginx 루트 디렉터리의 nginx.exe를 등록

6. php의 경우 php 루트 디렉터리의 php-cgi.exe를 등록하고 Arguments에 -b 127.0.0.1:9000를 등록