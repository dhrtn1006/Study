
1. MySQL 홈페이지 - DOWNLOADS - Yum Repository에 접속

    `https://dev.mysql.com/downloads/repo/yum/`

2. 버전을 선택하여 다운로드를 클릭한다.

3. No thanks, just start my download. 를 우클릭하여 링크를 복사한다.

4. wget과 복사한 링크를 이용하여 rpm 파일을 다운로드 받는다.

    `wget https://dev.mysql.com/get/mysql80-community-release-el7-1.noarch.rpm`

5. rpm을 이용하여 다운로드 받은 파일을 repo에 등록한다.

    `rpm -ivh mysql80-community-release-el7-1.noarch.rpm`

6. repo에 정상적으로 등록 되었는지 확인한다.

    `yum repolist all | grep mysql`

7. enabled 항목이 다운로드 활성화된 항목이다.

8. 원하는 항목이 enabled 되지 않았을 경우 repo를 수정한다.

    `vi /etc/yum.repos.d/mysql-community.repo`

9. 원하는 버전의 enabled에 1을 그렇지 않은 버전의 enabled에 0을 입력한다.

10. yum으로 MySQL을 설치한다.

    `yum install mysql-server`

11. 버전이 맞는지 확인하고 설치완료한다.

12. systemctl start mysqld 명령어로 mysql을 실행시킨다.

13. /var/log/mysqld.log 파일에서 초기 비밀번호를 확인 후 로그인한다.

14. 비밀번호를 재설정한다.

    `ALTER USER 'root'@'localhost' IDENTIFIED BY 'root-password';`

15. root 사용자의 비밀번호는 12자 이상이어야 하고, 대문자, 소문자, 숫자, 특수문자를 하나 이상씩 포함해야한다.
