1. nodejs 확인 및 설치

    ```
    node -v

    yum install nodejs
    ```

2. nodejs 설치 시 npm도 같이 설치 되었는지 확인 후 미설치 시 npm 설치

    ```
    npm -v

    yum install npm
    ```

3. yarn 전역 설치

    ```
    npm install -g yarn

    # -g 옵션은 전역설치를 위해 추가
    ```

4. create-react-app 전역 설치

    ```
    npm install -g create-react-app
    ```

5. tar version이 낮아서 에러가 발생 할 경우 조치 방법

    ```
    #This version of tar is no longer supported,

    #and will not receive security updates. Please upgrade asap.

    npm install tar@6 -g
    ```

6. 원하는 위치에 react 프로젝트 설치

    ```
    create-react-app appname
    ```

7. react 프로젝트 build

    ```
    yarn build
    ```

8. nginx root 경로를 build 폴더로 변경 후 재시작