# gark  [![Travis CI](https://travis-ci.org/7Ethan/stress.svg?branch=master)](https://travis-ci.org/7Ethan/stress)  [![Go Report Card](https://goreportcard.com/badge/7Ethan/stress)](https://goreportcard.com/report/7Ethan/stress) 


gwrk is an HTTP stress testing tool inspired by [hey](https://github.com/rakyll/hey). Through this tool, you can do a stress test on the HTTP service and get detailed test results. 

## Installation

```
go get -u github.com/7Ethan/gark
```
 
## Features
 
* **Transactional task support**
* **Support duration and total number of requests**
* **Support package reference**
* **Support custom event**
* **Support customizable**
  
## Usage

gwrk contains two usage, either via the command line or used as a package.

### 1.Use command line.

```
Usage: gwrk [options...] <url> || gwrk [options...] -enable-tran <urls...>

Options:
  -n  Number of requests to run. Default value is 100.
      If set to -1, the request has been sent, but the report will 
      not be output by default.
  -c  Number of requests to run concurrently. 
      Total number of requests cannot smaller than the concurrency level. 
      Default value is 0.
  -d  Duration of requests to run. Default value is 0 sec.
  -o  Output file path. For example: /home/user or ./files.
  
  -h  Custom HTTP header. For example: 
      -h "Accept: text/html" -h "Content-Type: application/xml".
  -m  HTTP method, any of GET, POST, PUT, DELETE, HEAD, OPTIONS.
  -t  Timeout for each request in seconds. Default value is 20, 
      use 0 for infinite.
  -b  HTTP request body.
  -B  HTTP request body from file. For example:
      /home/user/file.txt or ./file.txt.
  -x  HTTP Proxy address as host:port.

  -h2 	 Enable HTTP/2.
  -host	 Set HTTP Host header.
  
  -think-time           Time to think after request. Default value is 0 sec.
  -disable-compression  Disable compression.
  -disable-keepalive    Disable keep-alive, prevents re-use of TCP
                    	connections between different HTTP requests.
  -disable-redirects    Disable following of HTTP redirects.
  -enable-tran          Enable transactional requests. Multiple urls 
                        form a transactional requests. 
                        For example: "stress [options...] -enable-tran 
                        http://localhost:8080,m:post,b:hi,x:http://127.0.0.1:8888 
                        http://localhost:8888,m:post,B:/home/file.txt,thinkTime:2 
                        [urls...]".
```

For example: run a task.

```
gwrk -n 1000 -c 10 -m GET http://localhost:8080
```

For example: run a transactional request composed of multiple URL.

```
gwrk -n 1000 -c 10 -enable-tran http://localhost:8080,m:post,b:hi,x:http://127.0.0.1:8888 http://localhost:8888,m:post,B:/home/file.txt,thinkTime:2 
```

 ### 2.Use package.

>TODO

## License

stress source code is licensed under the Apache Licence, [Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).
