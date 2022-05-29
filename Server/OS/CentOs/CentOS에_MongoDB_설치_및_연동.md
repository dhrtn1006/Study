1. php-pear 설치확인 및 설치

    ```
    pecl version
    ```

    ```
    yum install php-pear
    ```

2. pecl로 mongodb 설치

    ```
    pecl install mongodb
    ```

3. php.ini 파일에 extension 추가

    ```
    vi etc/php.ini
    ```

    ```
    extension=mongodb.so
    ```

4. mongoDB 실행

    ```
    mongo
    ```

5. admin DB로 이동하여 관리자 권한을 추가

    ```
    use admin
    ```

    ```
    db.createUser({
        user: "root",
        pwd: "PASSWORD",
        roles: ["userAdminAnyDatabase"]
    })
    ```

6. 권한 부여를 위해 conf 파일에 security 주석을 제거하여 authorization을 활성화

    ```
    vi /etc/mongod.conf
    ```

    ```
    security:
        authorization: enabled
    ```

7. 재접속 후 auth를 이용하여 root 권한을 획득

    ```
    use admin
    ```

    ```
    db.auth("root", "PASSWORD" )
    ```

8. 사용할 DB를 선택하여 읽기 / 쓰기 권한을 가진 유저를 생성

    ```
    use <useDB>
    ```

    ```
    db.createUser({
        user: "<username>",
        pwd: "<password>",
        roles: ["readWrite"]
    })
    ```

9. 재접속 후 생성한 DB로 이동하여 권한을 획득

    ```
    use <useDB>
    ```

    ```
    db.auth("<username>", "<password>" )
    ```