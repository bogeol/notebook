## 大概

- xhr【XMLHttpRequest】
- ajax
- axios

## xhr

- https://zh.javascript.info/xmlhttprequest

`XMLHttpRequest` 是一个内建的浏览器对象，它允许使用 JavaScript 发送 HTTP 请求。

```
// 1. 创建一个 new XMLHttpRequest 对象
let xhr = new XMLHttpRequest();

// 2. 配置它：从 URL /article/.../load GET-request
xhr.open('GET', '/article/xmlhttprequest/example/load');

// 3. 通过网络发送请求
xhr.send();

// 4. 当接收到响应后，将调用此函数
xhr.onload = function() {
  if (xhr.status != 200) { // 分析响应的 HTTP 状态
    alert(`Error ${xhr.status}: ${xhr.statusText}`); // 例如 404: Not Found
  } else { // 显示结果
    alert(`Done, got ${xhr.response.length} bytes`); // response 是服务器响应
  }
};
```

> 现如今，我们有一个更为现代的方法叫做 `fetch`，它的出现使得 `XMLHttpRequest` 在某种程度上被弃用。

## ajax

- https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX
- https://api.jquery.com/jquery.ajax/

AJAX stands for **A**synchronous **J**avaScript **A**nd **X**ML.

 In a nutshell, it is the use of the `XMLHttpRequest` object to communicate with servers. 

It can send and receive information in various formats, including JSON, XML, HTML, and text files. 

AJAX’s most appealing characteristic is its "asynchronous" nature, which means it can **communicate with the server**, exchange data, and update the page **without having to refresh the page**.【**异步请求**】

常用的jQuery的ajax：

```javascript
$.ajax({
  method: "POST",
  url: "some.php",
  data: { 
      name: "John", 
      location: "Boston" 
  }
}).done(function (msg) {
    alert( "Data Saved: " + msg );
});
```

## axios

- https://github.com/axios/axios

axios：Promise based HTTP client for the browser and node.js

features:

- Make [XMLHttpRequests](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) from the browser
- Make [http](http://nodejs.org/api/http.html) requests from node.js
- Supports the [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) API
- Intercept request and response
- Transform request and response data
- Cancel requests
- Automatic transforms for JSON data
- Client side support for protecting against [XSRF](http://en.wikipedia.org/wiki/Cross-site_request_forgery)

```
// GET
axios({
  method: 'get',
  url: 'http://bit.ly/2mTM3nY',
  responseType: 'stream'
})
.then(function (response) {
	console.log(response);
});
  
  
// POST
axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Fred',
    lastName: 'Flintstone'
  }
}).then(function (response) {
	console.log(response);
});
```

### url本地和部署到服务器上的区别【也就是没有前缀的时候是咋的】

```
axios({
  method: 'get',
  url: '/api/users', # url自动补全请求的服务器地址（猜测）
})
```

- [ ] axios放到vuejs中使用
  - [ ] 使用axios定义一个通用request或者放到vue原型中
  - [ ] 设置axios配置【baseURL / 跨域等】

### axios params / data【url参数 / req body参数】

- params - 链接参数
- data - 请求体参数

```
  // `params` are the URL parameters to be sent with the request 【params ~ url参数】
  // Must be a plain object or a URLSearchParams object
  params: {
    ID: 12345
  },
```

```
 // `data` is the data to be sent as the request body【data ~ json参数 / req body参数】
  // Only applicable for request methods 'PUT', 'POST', 'DELETE , and 'PATCH'
  // When no `transformRequest` is set, must be of one of the following types:
  // - string, plain object, ArrayBuffer, ArrayBufferView, URLSearchParams
  // - Browser only: FormData, File, Blob
  // - Node only: Stream, Buffer
  data: {
    firstName: 'Fred'
  },
```

