## Performance Benchmarks

In this article, we will learn how to build a simple REST API using Go, Python, and Node.js. We will also learn how to benchmark the performance of our API endpoints using Apache Benchmark tool.

## Prerequisites

- [Go](https://golang.org/dl/)
- [Python](https://www.python.org/downloads/)
- [Node.js](https://nodejs.org/en/download/)
- [Apache Benchmark](https://httpd.apache.org/docs/2.4/programs/ab.html)

## Building a REST API

### Go

- Create a new directory for our Go project:

```bash

mkdir go-rest-api

cd go-rest-api

```

- Create a new file named `main.go` and add the following code:

```go

package main

import (
    "net/http"
)

func main() {

    http.HandleFunc("/ping", func(w http.ResponseWriter, r *http.   Request) {

        w.Write([]byte("pong"))
    })

    http.ListenAndServe(":8080", nil)
}

```

- Run the following command to build and run our Go project:

```bash

go run main.go

```

- Open a new terminal and run the following command to test our `/ping` endpoint:

```bash

curl http://localhost:8080/ping

```

- The output should be:

```bash


pong

```

### Python

- Create a new directory for our Python project:

```bash

mkdir python-rest-api

cd python-rest-api

```

- Create a new file named `main.py` and add the following code:

```python

from flask import Flask

app = Flask(__name__)

@app.route("/ping", methods=["GET"])

def ping():
    return "pong"

if __name__ == "__main__":

app.run()

```

- Run the following command to install Flask:

```bash

pip install flask

```

- Run the following command to build and run our Python project:

```bash

python main.py

```

- Open a new terminal and run the following command to test our `/ping` endpoint:

```bash

curl http://localhost:5000/ping

```

- The output should be:

```bash


pong

```

### Node.js

- Create a new directory for our Node.js project:

```bash

mkdir nodejs-rest-api

cd nodejs-rest-api

```

- Create a new file named `main.js` and add the following code:

```javascript
const express = require("express");

const app = express();

app.get("/ping", (req, res) => {
  res.send("pong");
});

app.listen(3000, () => {
  console.log("Server is running on port 3000.");
});
```

- Run the following command to install Express:

```bash

npm install express

```

- Run the following command to build and run our Node.js project:

```bash

node main.js

```

- Open a new terminal and run the following command to test our `/ping` endpoint:

```bash

curl http://localhost:3000/ping

```

- The output should be:

```bash


pong

```

## Benchmarking the Performance

We conducted a benchmark test for our `/ping` endpoint using Apache Benchmark tool with the following specifications:

- Document Path: `/ping`
- Document Length: 4 bytes
- Concurrency Level: 10
- Total requests: 1,000,000
- Here are the results of our benchmark test:

These results indicate that our `/ping` endpoint is performing well under high load with a high number of concurrent requests. However, it is important to note that the performance may vary depending on the system specifications and network conditions.

| Framework         | Concurrency Level | Time taken for tests (seconds) | Complete requests | Failed requests | Total transferred (bytes) | HTML transferred (bytes) | Requests per second (mean) | Time per request (mean) | Time per request (mean, across all concurrent requests) | Transfer rate (Kbytes/sec) |
| ----------------- | ----------------- | ------------------------------ | ----------------- | --------------- | ------------------------- | ------------------------ | -------------------------- | ----------------------- | ------------------------------------------------------- | -------------------------- |
| Go (net/http)     | 10                | 40.917                         | 1000000           | 0               | 120000000                 | 4000000                  | 24439.90                   | 0.409 ms                | 0.041 ms                                                | 2864.05                    |
| Python (Flask)    | 10                | 1123.621                       | 1000000           | 0               | 176000000                 | 4000000                  | 889.98                     | 11.236 ms               | 1.124 ms                                                | 152.97                     |
| Node.js (Express) | 10                | 166.324                        | 1000000           | 0               | 202000000                 | 4000000                  | 6012.35                    | 1.663 ms                | 0.166 ms                                                | 1186.03                    |

* NOTE: The results may vary depending on the system specifications and network conditions.

## Conclusion

In this article, we have learned how to build a simple REST API using Go, Python, and Node.js. We have also learned how to benchmark the performance of our API endpoints using Apache Benchmark tool. We hope that this article will help you to build your own REST API.

## References

- [Go net/http package](https://golang.org/pkg/net/http/)

- [Python Flask](https://flask.palletsprojects.com/en/1.1.x/)

- [Node.js Express](https://expressjs.com/)

- [Apache Benchmark](https://httpd.apache.org/docs/2.4/programs/ab.html)
