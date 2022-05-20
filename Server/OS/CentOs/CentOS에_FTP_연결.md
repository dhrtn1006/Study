1. 리눅스 서버에 vsftp 프로그램이 설치되어 있는지 확인

    `rpm -qa vsftpd*`

2. vsftp 프로그램을 설치한다.

    `yum install vsftpd -y`

3. vsftp 설정을 변경한다.

    `vi /etc/vsftpd/vsftpd.conf`

4. 모두 지우고 아래 내용으로 대체

    ```    
    anonymous_enable=NO 

    local_enable=YES 

    write_enable=YES 

    local_umask=022 

    dirmessage_enable=YES 

    xferlog_enable=YES 

    connect_from_port_20=YES 

    xferlog_file=/var/log/xferlog 

    xferlog_std_format=YES 

    chroot_local_user=YES 

    listen=YES 

    pam_service_name=vsftpd 

    userlist_enable=YES 

    tcp_wrappers=YES
    ```

5. 공백이 있으면 status=2 오류가 난다.

4. vsftpd 시작

    `systemctl start vsftpd`

5. 재부팅 시 자동 시작하도록 설정

    `systemctl enable vsftpd`

6. 사용하고자 하는 user의 접속 거부 리스트 계정을 풀어준다.

    `vi /etc/vsftpd/ftpusers`

    `vi /etc/vsftpd/user_list`

7. vsftpd 재시작

    `systemctl restart vsftpd`

8. 500 oop 에러가 나는 경우 conf 파일에 항목 추가

    ```
    chroot_list_enable=YES

    chroot_list_file=/etc/vsftpd/chroot_list

    ```

9. /etc/vsftpd 폴더 내부에 chroot_list 파일을 생성하고 내용에 root를 넣는다.
​