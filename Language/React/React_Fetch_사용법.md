React Fetch 사용법

1. Fetch 기본 문법

    ```
    fetch(url, [option])

    .then(function (response) { return response.json() })

    .then(function (json) { console.log(json) })

    .catch((error) => console.log("error:", error));
    ```

2. Fetch Option 문법

    ```
    fetch(url, , {

        method: "POST",

        headers: {

            'Content-type': 'application/json'

        },

        body: JSON.stringify({

            dataA: "dataA",

            dataB: "dataB"

        })

    })


    # GET 방식일 경우 Option을 생략 할 수 있다.
    ```