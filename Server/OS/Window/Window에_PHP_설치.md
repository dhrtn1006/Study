1. PHP 홈페이지에서 원하는 버전의 Non Thread Safe 타입 zip 파일을 다운로드받는다.

    `https://windows.php.net/download`

2. 다운로드 받은 zip 파일을 원하는 경로(c드라이브 내부)에 두고 압축을 해제한다.

3. php.ini-development 파일을 php.ini로 변경하고 extension_dir = "ext" 주석을 해제한다.

4. php 루트경로에서 cmd를 실행하고 php-cgi -b 127.0.0.1:9000 를 입력해서 php를 실행시킨다.