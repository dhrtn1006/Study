1. Github 홈페이지에서 Repository를 생성한다.

2. 프로젝트 경로를 생성하고 Git을 init한다.

    ```
    echo "# project start" >> README.md

    git init

    git add README.md

    git commit -m "first commit"

    git branch -M main

    git remote add origin (Repository 주소)

    git push -u origin main
    ```

3. 다른 경로에 해당 프로젝트를 가져오고 싶을 경우 clone을 사용한다.

    `git clone (Repository 주소)`

4. 프로젝트 수정 전 최신 프로젝트를 가져오고 싶을 경우 pull을 사용한다.

    `git pull origin master`

5. 프로젝트 수정 시 status로 상태 확인 후 add > commit > push 순으로 진행한다.

    ```
    git status

    git add .

    git commit -m "commit msg"

    git push origin main
    ```

6. 여러 사람이 함께 프로젝트를 진행할때 브랜치별로 나누어 작업이 가능하다.

    ```
    git branch one

    git branch two

    git branch three ...
    ```

7. remote Repository 변경

    7.1 remote 제거

        git remote remove origin

    7.2 새 remote 추가

        `git remote add origin (Repository 주소)`

    7.3 Repository 생성 후 remote 추가

        ```
        git remote add origin  (Repository 주소)

        git branch -M main

        git push -u origin main
        ```
