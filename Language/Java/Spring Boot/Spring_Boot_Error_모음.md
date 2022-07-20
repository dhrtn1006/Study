1. 디버그 출력 비활성화 에러

    1-1. Error Msg

    ```
    Error starting ApplicationContext. To display the conditions report re-run your application with 'debug' enabled.
    ```

    1-2. 구성편집 > 옵션수정 > 디버그 출력 활성화

2. DB 미연결 에러

    2-1. Error Msg

    ```
    Failed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.

    Reason: Failed to determine a suitable driver class
    ```
    
    2-2. build.gradle을 통해 Spring Boot를 DataBase에 연결해준다.