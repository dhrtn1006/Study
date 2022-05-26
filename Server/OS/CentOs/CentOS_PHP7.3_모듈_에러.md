1. 에러 코드

    ```
    /usr/lib64/php/modules/zip.so.so: cannot open shared object file: No such file or directory
    ```

2. PHP 7.3 버전에서 yum 으로 php-zip 설치 시 zip 확장 모듈이 누락되는 문제가 발생

3. php-devel과 php-pear를 설치한다.

    ```
    yum install php-devel php-pear
    ```

4. 기존의 php-zip 모듈 확인 후 삭제

    ```
    yum list installed | grep php
    ```

5. pecl로 zip 모듈 설치

    ```
    pecl install zip
    ```

6. php.ini 파일에 extension 추가 후 재실행

    ```
    extension=zip.so
    ```
