1. php 설치 확인

    `php -v , - yum list php`

2. php 제거

    `yum remove php*`

3. php 최신 안정버전 rpm repo 등록

    `wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm`

    `rpm -Uvh epel-release-latest-7.noarch.rpm`

    `wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm`

    `rpm -Uvh remi-release-7.rpm`

4. repo 등록 확인

    `yum repolist all | grep php`

5. 설치할 버전 선택

    `vi /etc/yum.repos.d/remi-php73.repo`

    `enabled = 1`

6. php 설치

    `yum install php php-mysql php-mbstring php-pdo php-gd php-fpm`

7. php lib 설치

    `yum install libjpeg* libpng* freetype* gd-* gcc gcc-c++ gdbm-devel libtermcap-devel`