1. Homebrew에 접속하여 메인에 있는 설치 소스로 다운로드받는다

    `https://brew.sh/`

2. 맥북 M1에서는 /home 내부에 자동 실행 명령어가 있어야 Homebrew가 실행된다.

    `vi ~/.zshrc`

    `eval $(/opt/homebrew/bin/brew shellenv)`

3. Homebrew로 Nginx를 다운받는다.

    `brew install nginx`

4. Nginx 설치 폴더로 접근해서 conf파일을 수정한다.

    `vi /opt/homebrew/etc/nginx/nginx.conf`

    ```
    server {

        listen 8080;

        server_name localhost;

        root 원하는 루트 디렉터리;

       location / {

            index index.html index.htm index.php;

        }

       error_page 500 502 503 504 /50x.html;

            location = /50x.html {

            root html;

        }

        location ~ \.php$ {

            fastcgi_pass 127.0.0.1:9000;

            fastcgi_index index.php;

            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;

            include fastcgi_params;

        }

    }
    ```

5. Homebrew로 원하는 버전의 PHP를 설치한다.

    `brew install php@7.4`

6. Nginx와 PHP를 재실행한다.

    `brew services restart nginx`

    `brew services restart php`