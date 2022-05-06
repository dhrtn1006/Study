1. nginx 설치 확인

    `nginx -v , - yum list nginx`

2. nginx repo 추가

    `vi /etc/yum.repos.d/nginx.repo`

3. repo 내용 추가

    `[nginx]`

    `name=nginx  repo`

    `baseurl=http://nginx.org/packages/centos/$releasever/$basearch/`

    `gpgcheck=0`

    `enabled=1`
​
4. yum 업데이트 후 nginx 다운로드

    `yum update`

    `yum install nginx`