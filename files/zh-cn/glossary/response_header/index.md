---
title: Response header 响应头
slug: Glossary/Response_header
---

**响应头（Response header）** 可以定义为：被用于 http 响应中并且和响应消息主体无关的那一类 {{glossary("header", "HTTP header")}}。像{{HTTPHeader("Age")}}, {{HTTPHeader("Location")}} 和 {{HTTPHeader("Server")}}都属于响应头，他们被用于描述响应。

并非所有出现在响应中的 http header 都属于响应头，例如{{HTTPHeader("Content-Length")}}就是一个代表响应体消息大小的{{glossary("entity header")}}，虽然你也可以把它叫做响应头。

下面展示了一个 {{HTTPMethod("GET")}}请求的响应头。需要注意的是，严格来说{{HTTPHeader("Content-Encoding")}}和{{HTTPHeader("Content-Type")}}都是属于{{glossary("entity headers")}}。

```
200 OK
Access-Control-Allow-Origin: *
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Mon, 18 Jul 2016 16:06:00 GMT
Etag: "c561c68d0ba92bbeb8b0f612a9199f722e3a621a"
Keep-Alive: timeout=5, max=997
Last-Modified: Mon, 18 Jul 2016 02:36:04 GMT
Server: Apache
Set-Cookie: mykey=myvalue; expires=Mon, 17-Jul-2017 16:06:00 GMT; Max-Age=31449600; Path=/; secure
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding
X-Backend-Server: developer2.webapp.scl3.mozilla.com
X-Cache-Info: not cacheable; meta data too large
X-kuma-revision: 1085259
x-frame-options: DENY
```

## 更多

### 相关内容

- [HTTP 头部列表](/zh-CN/docs/Web/HTTP/Headers)
