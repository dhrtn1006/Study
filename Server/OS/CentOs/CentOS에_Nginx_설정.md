
1. Nginx 설정파일 경로

    CentOS7
    
    `/etc/nginx/conf.d/default.conf`

    CentOS8

    `/etc/nginx/conf/nginx.conf`

2. 보안을 위해 ip 접속을 차단한다.

    ```
    server {
        listen       80;
        server_name  255.255.255.255;
        return 404;
    }
    ```

3. 관리를 위해 도메인별 conf를 만들어 관리한다.

4. conf 파일 내부 server 예제

    CentOS7

    ```
    server { 

        listen       80; 

        server_name  localhost; 

        root /var/www/html;


        location / { 

            index  index.html index.htm index.php; 

        } 


        error_page   500 502 503 504  /50x.html; 

        location = /50x.html { 

            root /usr/share/nginx/html; 

        } 

    ​

        location ~ \.php$ { 

            fastcgi_pass   127.0.0.1:9000; 

            fastcgi_index  index.php; 

            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name; 

            include        fastcgi_params; 

        } 

    ​

        if (!-e $request_filename ) { 

            rewrite ^(.*)$ /index.php last; 

        } 

    } 
    ```​

    CentOS8

    ```
    http {

        ...

        server { listen 80; server_name  localhost; ... }

        server { listen 81; server_name  localhost; ... }

        server { listen 80; server_name  domain.com www.domain.com; ... }

    }
    ```

5. php-fpm 서버 파일을 수정한다.

    `vi /etc/opt/remi/php74/php-fpm.d/www.conf`

    `vi /etc/php-fpm.d/www.conf`

6. 초기 설치 시 Apache로 세팅되는데 이것을 전부 nginx로 변경한다.

7. php-fpm과 nginx 연동 경로를 nginx 서버 파일과 동일하게 설정한다. (포트 포함)

    ```
    user = nginx

    group = nginx

    listen.owner = nginx

    listen.group = nginx

    listen.acl_users = nginx

    listen = 127.0.0.1:9000
    ```