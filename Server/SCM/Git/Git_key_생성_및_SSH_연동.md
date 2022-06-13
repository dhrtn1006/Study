1. 키 파일 (공개 키와 비밀 키) 을 생성한다.

    ```
    ssh-keygen -t ed25519 -C "your_email@example.com"

    Enter file in which to save the key (/Users/User/.ssh/id_ed25519): [Key File 저장 위치 ex) /Users/User/.ssh/Key File Name]

    Enter passphrase (empty for no passphrase): [Key File Password / Password가 없을 경우 공백]

    Enter same passphrase again: [Password Same Check]
    ```

2. 키 파일 경로에 config 파일 생성

    ```
    Host *

    IgnoreUnknown UseKeychain
    ```

3. ssh-agent에 Key 등록

    ```
    eval "$(ssh-agent -s)"

    ssh-add -K ~/.ssh/Key File Name
    

    # eval "$(ssh-agent -s)" 명령어를 실행하지 않고 ssh-add 시 Could not open a connection to your authentication agent. 에러 발생


    # Key File에 Password 설정 시 ssh-add 명령어에 -K 옵션을 추가할 경우 Password를 묻지 않아

    - Provider "internal" returned failure -4

    - Unable to load resident keys: device not found 에러 발생
    ```

4. github에 SSH Key 추가

    ```
    Setting > SSH and GPG keys > new SSH key

    원하는 Title을 입력하고 Key에 생성한 공개키 (Key File Name.pub) 내용을 입력
    ```

5. Key 등록 테스트

    ```
    ssh -T git@github.com

    # Hi schooldevops! You've successfully authenticated, but GitHub does not provide shell access. 문구 출력 시 성공
    ```