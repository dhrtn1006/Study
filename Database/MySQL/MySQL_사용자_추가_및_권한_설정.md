1. MySQL 사용자 추가

    ```
    create user 'username'@'localhost' identified by 'userpassword';

    create user 'username'@'%' identified by 'userpassword';
    ```
    
2. MySQL 사용자 권한 설정

    ```
    grant all privileges on database.* to 'username'@'localhost';

    grant all privileges on database.* to 'username'@'%';
    ```