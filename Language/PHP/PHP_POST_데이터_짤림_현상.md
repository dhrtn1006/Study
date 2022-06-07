1. PHP AJAX 통신 시 POST 방식을 사용하여 JSON 데이터를 보낼 때 전송되는 데이터가 누락되는 현상이 발생

2. `upload_max_filesize` 와 `post_max_size` 값이 적어서 발생

3. CentOS의 DDOS 보안을 위한 yum 자동 업데이트로 인해 PHP 또한 업데이트되면서 `max_input_vars` 값이 추가

4. `max_input_vars`의 기본값이 1000인데 그로인해 STRING 값으로 넘어가는 POST 데이터가 누락

5. php.ini 파일에 `max_input_vars` 항목을 찾아서 주석 제거하고 원하는 값으로 변경

6. `max_input_vars` 항목이 없다면 추가