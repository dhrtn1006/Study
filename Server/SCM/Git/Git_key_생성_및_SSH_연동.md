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

    # Provider "internal" returned failure -4

    # Unable to load resident keys: device not found 에러 발생


    # Linux에서 등록 시 Key File 의 권한을 400으로 설정

    # 그렇지 않을 경우 WARNING: UNPROTECTED PRIVATE KEY FILE! 에러 발생
    ```

4. github에 SSH Key 추가

    4-1. 해당 github 계정에 Public Key 추가

    ```
    Setting > SSH and GPG keys > new SSH key

    # 원하는 Title을 입력하고 Key에 생성한 공개키 (Key File Name.pub) 내용을 입력
    ```
    
    4-2. 계정 내부의 Repository에 Public Key 추가

    ```
    Repository > Setting > Deploy keys > Add deploy key

    # 원하는 Title을 입력하고 Key에 생성한 공개키 (Key File Name.pub) 내용을 입력 후 읽기/쓰기 권한 추가
    
    # Key를 추가한 Repository 외에 다른 Repository는 접근 불가
    ```

5. Key 등록 테스트

    ```
    ssh -T git@github.com
    
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

    # Hi schooldevops! You've successfully authenticated, but GitHub does not provide shell access. 문구 출력 시 성공
    ```
