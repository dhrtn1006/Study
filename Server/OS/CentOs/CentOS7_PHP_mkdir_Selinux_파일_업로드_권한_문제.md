1. CentOS7 Selinux Enforcing 상태일 때 PHP에서 mkdir 시 permission denied 에러가 발생

2. 저장 할 폴더의 권한 변경

    ```
    chmod -R 755 [path]
    ```

3. 파일을 저장 할 폴더의 소유자를 nginx로 변경 조치

    ```
    chown -R nginx [path]
    ```

4. Nginx 및 PHP-FPM 의 사용자명이 nginx 가 맞는지 확인

    ```
    vi /etc/nginx/nginx.conf

    => user nginx - check


    vi /etc/php-fpm.d/www.conf

    => user = nginx - check
    
    => group = nginx - check
    
    => listen.owner = nginx - check
    
    => listen.group = nginx - check
    
    => listen.acl_users = nginx - check
    ```

5. Nginx 및 PHP-FPM 재시작

    ```
    systemctl restart nginx

    systemctl restart php-fpm
    ```

6. PHP에서 mkdir 시 여전히 permission denied 에러가 발생

7. Selinux 일시 정지 후 업로드 확인

    ```
    getenforce

    // Selinux 상태확인 (Enforcing - 켜짐, permissive - 일시정지)

    setenforce 0

    // Selinux 일시정지
    
    setenforce 1

    // Selinux 일시정지 해제
    ```

8. Selinux 일시 정지 후 업로드 정상 작동

9. Selinux context 설정 확인

    ```
    ls -Z

    =>

    drwxr-xr-x. nginx root  unconfined_u:object_r:httpd_sys_content_t:s0 [dir]

    ```

10. 보안 정책으로 인해 WRIGHT 권한이 없는 상황

11. Selinux context 권한 재지정

    ```
    chcon -R -t httpd_sys_content_rw_t [dir]
    ```

12. Selinux 일시 정지 해제 후 업로드 테스트 => 정상작동