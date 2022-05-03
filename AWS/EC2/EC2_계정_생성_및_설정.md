1. EC2 인스턴스 생성 시 키페어를 설정하고 생성

2. 키페어를 이용해 최초 생성 유저인 ec2-user 계정으로 접속한다.

3. root 비밀번호를 지정한다.

	`sudo passwd root`

4. root 계정을 활성화한다.

    `su`

5. 새 사용자 계정을 추가한다.

	`adduser userID`

6. 새 사용자의 비밀번호를 설정한다.

7. 새 사용자의 계정에 ssh key를 생성한다.

	`cp -r /home/ec2-user/.ssh /home/userID`

	`cp -r : 하위 디렉토리 모두 복사`

8. ssh key의 소유자를 새 사용자로 변경한다.

	`chown -R userID:userID /home/userID/.ssh/`

	`chown -R : 하위 디렉토리 모두 변경`

9. sshd를 재시작한다.

	`systemctl restart sshd`

10. 최초 접속용 유저를 삭제한다.

	`userdel -r ec2-user`

	`userdel -r : 홈 디렉토리 포함 삭제`

	`userdel -f : 삭제 중 에러를 무시하고 강제 삭제`