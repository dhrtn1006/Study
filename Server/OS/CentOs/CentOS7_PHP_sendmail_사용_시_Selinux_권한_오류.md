1. PHP-sendmail 사용 시 SELinux 권한 오류 발생

    ```
    fatal: open /etc/postfix/main.cf: Permission denied
    ```

2. Nginx가 메일을 보낼 수 있는 SELinux 권한이 있는지 확인

    ```
    getsebool httpd_can_sendmail
    ```

3. 권한이 있을 경우

    ```
    httpd_can_sendmail --> on
    ```

4. 권한이 없을 경우

    ```
    httpd_can_sendmail --> off
    ```

5. 권한이 없을 경우 활성화한다.

    ```
    setsebool -P httpd_can_sendmail 1
    ```