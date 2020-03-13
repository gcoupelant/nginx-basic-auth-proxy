# Docker image of Nginx Proxy with Basic Auth login

Simple HTTP Proxy to connect to a server with Basic Authentication

```
          +------------------------+   w/ user:pass   +-------------+
User ---> | nginx-basic-auth-proxy | ---------------> | HTTP Server |
          +------------------------+                  +-------------+
```

## Run

```bash
$ docker run \
    --rm \
    --name nginx-basic-auth-proxy \
    -p 8080:80 \
    -e BASIC_AUTH_USERNAME=username \
    -e BASIC_AUTH_PASSWORD=password \
    -e PROXY_PASS=https://www.website-with-basic-auth.com \
    -e PORT=80 \
    gcoupelant/nginx-basic-auth-proxy
```

Access to http://localhost:8080, then browser won't ask you username and password.

## Environment variables

### Required

|Key|Description|
|---|---|
|`BASIC_AUTH_USERNAME`|Basic auth username|
|`BASIC_AUTH_PASSWORD`|Basic auth password|
|`PROXY_PASS`|Proxy destination URL|

### Optional

|Key|Description|Default|
|---|---|---|
|`SERVER_NAME`|Value for `server_name` directive|`example.com`|
|`PORT`|Value for `listen` directive|`80`|
|`WORKER_PROCESSES`|Value for `worker_processes` directive|`auto`|

## Author

Daisuke Fujita ([@dtan4](https://github.com/dtan4))

## License

[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)
