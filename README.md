# Instructions

In this task, you need to write a simple HTTP Denial-of-Service protection system.
The solution should reside in different modules (one for the server, one for the client).

1. Client
   
   * CLI application.
   * The user enters the number of HTTP clients to simulate (as CLI args).
   * Each HTTP client should do the following:
      - Send HTTP request to a server with client identifier as a query parameter (e.g. http://localhost:8080/?clientId=3).
      - After the request done, wait some random time and then send another request (with same client id).
      - The HTTP clients should run simultaneous (concurrently) without blocking each other.
   * The client will run until key press after which it will gracefully drain all the requests (wait for all the of them to complete) and will exit.

2. Server
   * An HTTP server, using any stack you'd like.
   * Endpoint that for each incoming HTTP request you will do the following:
      - Check if this specific client reached the max number of requests per time frame threshold (no more than 5 requests per 5 secs).
      - If the client hasn’t reached the threshold, it will get “200 OK” response otherwise “503 Service Unavailable”.
      - Note: The time frame starts on each client’s first request and ends 5 seconds later. After the time frame has ended, the client’s first request will open a new time frame and so forth.

General notes:
* You're allowed using any web framework, HTTP client, etc. You're expected to choose the tools you're most familiar with and use best practices.
* The solution should be clean piece of code – please write it as it was a production code (use your own standards/conventions).
* Pay attention to thread safeness.
* The solution should be as simple as possible (avoid over design/engineering).

## Requirements

- [Go](https://golang.org/)

## Install 

Navigate to %GOPATH/src
```
git clone https://github.com/mali8/httpServerDenial.git
cd httpServerDenial
go install
```

## Usage

Run server
```
httpServerDenial server
```

Run client
```
httpServerDenial client 5
```

## Tests

Navigate to %GOPATH/src/httpServerDenial
```
go test -v ./server/
```

Author: Nejc Belšak

E-mail: belsak@gmail.com
