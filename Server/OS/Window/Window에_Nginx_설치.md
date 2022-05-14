1. Nginx 홈페이지에서 Stable 버전의 Window용 Nginx를 다운로드한다.

`https://nginx.org/en/download.html`

2. 다운로드 받은 zip 파일을 원하는 경로에 두고 압축을 해제한다.

3. 포트와 서버네임을 지정, root 경로를 location 밖으로 빼내고 fastcgi의 주석을 해제한다.

    ```
    server {

        listen       80;

        server_name  255.255.255.255;

        root   html;

        location / {

            index  index.html index.htm index.php;

        }

        error_page   500 502 503 504  /50x.html;

        location = /50x.html {

            root   html;

        }

        location ~ \.php$ {

            fastcgi_pass   127.0.0.1:9000;

            fastcgi_index  index.php;

            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;

            include        fastcgi_params;

        }

    }
    ```​

4. 여러개의 포트를 개방할 경우 http 내부에 서로다른 포트의 server를 여러개 입력한다.

    ```
    http {

        ...

        server { listen 80; ... }

        server { listen 81; ... }

        server { listen 82; ... }

    }
    ```