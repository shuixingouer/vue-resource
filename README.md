#vue-resource

vue-resource是Vue.js的一款插件，它可以通过XMLHttpRequest或JSONP发起请求并处理响应。也就是说，$.ajax能做的事情，vue-resource插件一样也能做到，而且vue-resource的API更为简洁。另外，vue-resource还提供了非常有用的inteceptor功能，使用inteceptor可以在请求前和请求后附加一些行为，比如使用inteceptor在ajax请求时显示loading界面。

#vue-resource特点

 vue-resource插件具有以下特点：

 1. 体积小

 vue-resource非常小巧，在压缩以后只有大约12KB，服务端启用gzip压缩后只有4.5KB大小，这远比jQuery的体积要小得多。

 2. 支持主流的浏览器

 和Vue.js一样，vue-resource除了不支持IE 9以下的浏览器，其他主流的浏览器都支持。

 3. 支持Promise API和URI Templates

 Promise是ES6的特性，Promise的中文含义为“先知”，Promise对象用于异步计算。
 URI Templates表示URI模板，有些类似于ASP.NET MVC的路由模板。

 4. 支持拦截器

 拦截器是全局的，拦截器可以在请求发送前和发送请求后做一些处理。
 拦截器在一些场景下会非常有用，比如请求发送前在headers中设置access_token，或者在请求失败时，提供共通的处理方式。


#支持的HTTP方法
 vue-resource的请求API是按照REST风格设计的，它提供了7种请求API：
 
 get(url, [options])
 head(url, [options])
 delete(url, [options])
 jsonp(url, [options])
 post(url, [body], [options])
 put(url, [body], [options])
 patch(url, [body], [options])
 除了jsonp以外，另外6种的API名称是标准的HTTP方法。当服务端使用REST API时，客户端的编码风格和服务端的编码风格近乎一致，这可以减少前端和后端开发人员的沟通成本。

 客户端请求方法	        服务端处理方法
 this.$http.get(...)	Getxxx
 this.$http.post(...)	Postxxx
 this.$http.put(...)	Putxxx
 this.$http.delete(...)	Deletexxx
 options对象
 发送请求时的options选项对象包含以下属性：

 参数	类型	描述
 url	string	请求的URL
 method	string	请求的HTTP方法，例如：'GET', 'POST'或其他HTTP方法
 body	Object, FormData string	request body
 params	Object	请求的URL参数对象
 headers	Object	request header
 timeout	number	单位为毫秒的请求超时时间 (0 表示无超时时间)
 before	function(request)	请求发送前的处理函数，类似于jQuery的beforeSend函数
 progress	function(event)	ProgressEvent回调处理函数
 credentials	boolean	表示跨域请求时是否需要使用凭证
 emulateHTTP	boolean	发送PUT, PATCH, DELETE请求时以HTTP POST的方式发送，并设置请求头的X-HTTP-Method-Override
 emulateJSON	boolean	将request body以application/x-www-form-urlencoded content type发送

#response对象
  response对象包含以下属性：

  方法	类型	描述
  text()	string	以string形式返回response body
  json()	Object	以JSON对象形式返回response body
  blob()	Blob	以二进制形式返回response body
  属性	类型	描述
  ok	boolean	响应的HTTP状态码在200~299之间时，该属性为true
  status	number	响应的HTTP状态码
  statusText	string	响应的状态文本
  headers	Object	响应头
  注意：本文的vue-resource版本为v0.9.3，如果你使用的是v0.9.0以前的版本，response对象是没有json(), blob(), text()这些方法的。


 #使用resource服务

   vue-resource提供了另外一种方式访问HTTP——resource服务，resource服务包含以下几种默认的action：

   get: {method: 'GET'},
   save: {method: 'POST'},
   query: {method: 'GET'},
   update: {method: 'PUT'},
   remove: {method: 'DELETE'},
   delete: {method: 'DELETE'}
   resource对象也有两种访问方式：

   全局访问：Vue.resource
   实例访问：this.$resource




   博文链接：http://www.cnblogs.com/keepfool/p/5657065.html
