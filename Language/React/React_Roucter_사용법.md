React Roucter 사용법

1. npm이 최신버전인지 확인

    ```
    npm update
    ```

2. react router dom 설치

    ```
    npm install react-router-dom
    ```

3. react에서 라이브러리 호출

    ```
    import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
    ```

4. router 문법

    4-1. v6 이상

    ```
    <Router>
        <Header />
        <Routes>
            <Route path="/" element={<Home />} exact></Route>
            <Route path="/board" element={<Board />}></Route>
        </Routes>
        <Footer />
    </Router>
    ```

    4-2. v6 미만

    ```
    import { BrowserRouter as Router, Switch, Route } from "react-router-dom";
    <Router>
        <Header />
        <Switch>
            <Route path="/" exact><Home /></Route>
            <Route path="/Board"><Board /></Route>
        </Switch>
        <Footer />
    </Router>
    ```