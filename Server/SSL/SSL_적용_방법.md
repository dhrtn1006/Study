1. SSL 보안 인증서 신청

2. 인증 업체에서 인증메일 발송 (1~2시간)

3. 인증메일을 수신하고 인증완료 후 인증키 4가지 발급 (30분~1시간)

4. 개인키, 인증서(도메인), 체인인증서(중개자), 루트인증서(체인)

5. 인증키를 다운받아 서버로 이동

6. 개인키를 제외한 인증서-체인인증서-루트인증서 순서로 조합

    ```
    cat ssl.crt chain_ssl.crt chain_all_ssl.crt >  testdomain.com.crt
    ```

7. 인증서를 확인하여 줄바꿈 처리

    ```
    -----END CERTIFICATE----------BEGIN CERTIFICATE-----
    ```

    ```
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    ```

8. 개인키 복호화

    ```
    openssl rsa -in ssl.key -out app.1inmarket.co.kr.key
    ```

9. nginx.conf 파일을 수정

    ```
    server {

        # HTTP 접속 시 HTTPS로 리다이렉트

        listen       80;

        server_name  testdomain.com www.testdomain.com;

        root /var/www/html;


        location / {

            return 301 https://testdomain.com$request_uri;

        }

    }

    server {

        listen       443 ssl;

        server_name  testdomain.com www.testdomain.com;

        root /var/www/html;


        ssl_certificate     /etc/nginx/ssl/testdomain/testdomain.com.crt;

        ssl_certificate_key /etc/nginx/ssl/testdomain/testdomain.com.key;

        ....

    }
    ```

10. nginx를 재실행

11. 방화벽 설정에서 443포트를 개방

12. 인증서 갱신 시 인증서를 새로 발급받아 진행하므로 암호를 기억해두자.
