---
title: 同源策略  2018.06.03
tags: 跨域
notebook: 前端
---
<!-- TOC -->

- [同源策略: 所谓同源是指，域名，协议，端口相同。](#同源策略-所谓同源是指域名协议端口相同)
- [JSONP（JSON with Padding ） 跨域](#jsonpjson-with-padding--跨域)
    - [原理](#原理)
    - [实现代码](#实现代码)
- [CORS（Cross-Origin Resource Sharing） 跨域](#corscross-origin-resource-sharing-跨域)
    - [HTTP 响应首部字段](#http-响应首部字段)
    - [HTTP 请求首部字段](#http-请求首部字段)
- [postMessage 跨域](#postmessage-跨域)
    - [使用条件](#使用条件)
    - [发送消息](#发送消息)
    - [接受消息](#接受消息)

<!-- /TOC -->

## 同源策略: 所谓同源是指，域名，协议，端口相同。
- http://store.company.com:81/dir/page.html
- 协议: http
- 域名: store.company.com
- 端口: 81

## JSONP（JSON with Padding ） 跨域

### 原理
1. 由于 script img iframe 标签src属性不受同源策略影响，它们可以加载其他源中的资源
2. 创建 script 元素动态加载src js 脚本
3. callback 参数传递一个函数到后台执行js脚本
4. 只能get

### 实现代码
1. 前台
```
<script type="text/javascript">
    function jsonpCallback(result) {
        for(var i in result) {
            console.log(i+":"+result[i]);//循环输出a:1,b:2,c:3
        }
    }
</script>
<script type="text/javascript" src="http://crossdomain.com/services.php?callback=jsonpCallback"></script>
```
2. 后台js脚本
```
jsonpCallback({
    a: '1'
    b: '2'
    c: '3'
})
```

## CORS（Cross-Origin Resource Sharing） 跨域

### HTTP 响应首部字段
1. Access-Control-Allow-Origin
- origin 参数的值指定了允许访问该资源的外域 URI,*表示所有域都能访问
    > Access-Control-Allow-Origin: http://foo.example
2. Access-Control-Expose-Headers
- Access-Control-Expose-Headers 头让服务器把允许浏览器访问的头放入白名单，例如：
    > Access-Control-Expose-Headers: X-My-Custom-Header, X-Another-Custom-Header
3. Access-Control-Max-Age
- Access-Control-Max-Age 头指定了preflight请求的结果能够被缓存多久，请参考本文在前面提到的preflight例子。
    > Access-Control-Max-Age: 86400
3. Access-Control-Allow-Credentials
- 设置为 true 时需要附带身份凭证的请求。
    > Access-Control-Allow-Credentials: true
3. Access-Control-Allow-Methods
- Access-Control-Allow-Methods 首部字段用于预检请求的响应。其指明了实际请求所允许使用的 HTTP 方法。
    > Access-Control-Allow-Methods: POST, GET, OPTIONS
3. Access-Control-Allow-Headers
- Access-Control-Allow-Headers 首部字段用于预检请求的响应。其指明了实际请求中允许携带的首部字段。
    > Access-Control-Allow-Headers: X-PINGOTHER, Content-Type

### HTTP 请求首部字段
1. Origin
- Origin 首部字段表明预检请求或实际请求的源站
    > Origin: http://foo.example
1. Access-Control-Request-Method
- Access-Control-Request-Method 首部字段用于预检请求。其作用是，将实际请求所使用的 HTTP 方法告诉服务器。
    > Access-Control-Request-Method: POST
1. Access-Control-Request-Headers
- Access-Control-Request-Headers 首部字段用于预检请求。其作用是，将实际请求所携带的首部字段告诉服务器。
    > Access-Control-Request-Headers: X-PINGOTHER, Content-Type

## postMessage 跨域
### 使用条件
1. 相同的协议
2. 端口号和页面的模数 Document.domain设置为相同的值

### 发送消息
> otherWindow.postMessage(message, targetOrigin, [transfer]);
- otherWindow: 其他窗口的一个引用，比如iframe的contentWindow属性
- message: 将要发送到其他 window的数据
- targetOrigin: 控制消息可以发送到哪些窗口,eg:'*' or 'http://www.baidu.com:8080'
- transfer
### 接受消息
```
window.addEventListener("message", receiveMessage, false);

function receiveMessage(event)
{
  // For Chrome, the origin property is in the event.originalEvent
  // object.
  var origin = event.origin || event.originalEvent.origin; 
  if (origin !== "http://example.org:8080")
    return;

  // ...
}
```



