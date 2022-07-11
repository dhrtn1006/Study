1. resource 폴더를 프로젝트 폴더와 나누어 관리 할 경우 alias 를 사용

    nginx.conf

    ```
    location /resources {

        alias /var/www/html/homepage/resources;
        
    }
    ```

2. alias 사용 시 이미지 파일이 아닌 font 파일 등은 cros 이슈로 인해 불러오지 못하는 현상이 발생

    nginx.conf

    ```
    location /resources {

        add_header Access-Control-Allow-Origin *;

        alias /var/www/html/homepage/resources;
        
    }
    ```