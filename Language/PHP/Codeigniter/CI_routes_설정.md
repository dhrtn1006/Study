1. CI route로 REST를 구현 중 routes에 (:any) 사용 시 / 를 인식하지 못하는 문제 발생

2. 정규식으로 변경

    ```
    $route['URI/(any:)'] = 'URI';

    =>

    $route['URI/([a-zA-z0-9%\/]+)'] = 'URI';
    ```
