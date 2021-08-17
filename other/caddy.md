# Caddy

## Introduction

* 傳統使用nginx來做反向代理,使用Caddy可以更加快速地做使用

## Install

```
$ brew install caddy
```

## Usage

### Proxy

* 當網址輸入https://localhost:3002 ,會代理到port 3000的server
```
$ caddy reverse-proxy --from :3002 --to 127.0.0.1:3000
```

* 當不輸入時,會自動使用https://localhost 來做代理

```
$ caddy reverse-proxy --to 127.0.0.1:3000
```

### CaddyFile

* proxy
```
example.com {
    reverse_proxy 127.0.0.1:3002
    tls /usr/local/etc/nginx/ssl/server.crt /usr/local/etc/nginx/ssl/server.key
}
```

* static

```
*:8080 {
    root /path/to/html
    errors {
        404 404.html
    }
    gzip
    expires {
        match .html$ 1d
        match .xml$ 1d
        match .json$ 1d
    }
}
```

### 參考資料
1. [Caddy官方](https://caddyserver.com/docs/)
2. [Caddy教學](https://www.thepolyglotdeveloper.com/2018/07/serve-web-applications-minimal-effort-caddy/)