#### Node.js的组成部分
* **引入required模块**：可以使用require指令来载入Node.js模块。
* **创建服务器**：服务器可以监听客户端的请求
* **接收请求与响应请求**：使用浏览器和终端发送HTTP请求，服务器接收请求后返回响应数据。

#### Node.js事件循环
Node.js是单进程单线程应用程序，但是通过事件（观察者模式）和回调支持并发，所以性能非常高。
Node.js的每一个API都是异步的，并作为一个独立线程运行，使用异步函数调用，并处理并发。

### 事件驱动程序
Node.js使用事件驱动模型，当web server接收到请求，就把它关闭然后进行处理，然后去服务下一个web请求。
当这个请求完成，它被放回处理队列，当到达队列开头，这个结果被返回给用户。
这个模型非常高效可扩展性非常强，因为webserver一直接受请求而不等待任何读写操作。（非阻塞式IO/事件驱动IO）
在事件驱动模型中，会生成一个主循环来监听事件，当检测到事件时触发回调函数。

![event_loop.jpg](https://upload-images.jianshu.io/upload_images/11297430-26a7038b1f56fbee.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### EventEmitter
events模块只提供了一个对象：events.EventEmitter。EventEmitter的核心就是事情触发与事件监听器功能的封装。

#### Node.js Buffer
Buffer用来创建一个专门存放二进制数据的缓存区。

#### Node.js Stream
Stream(流)是一个抽象接口。
1. Stream四种流类型
* Readable(可读操作)
* Writable(可写操作)
* Duplex(可读可写操作)
* Transform(操作被写入数据，然后读出结果)
2. 所有的Stream对象都是EventEmitter的实例。常用的事情有：
* data：当有数据可读时触发。
* end：没有更多的数据可读时触发。
* error：在接收和写入过程中发生错误时触发。
* finish：所有数据已被写入到底层系统时触发。
3. 管道流
管道提供了一个输出流到输入流的机制。通常用于从一个流中获取数据并将数据传递到另一个流中。
->实现大文件的复制过程

![pipe.png](https://upload-images.jianshu.io/upload_images/11297430-53fadf3abd3f9f6d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4. 链式流
链式是通过连接输出流到另一个流并创建多个流操作链的机制。链式流一般用于管道操作。

#### Node.js模块系统
Node.js提供了exports和require两个对象，其中 exports是模块公开的接口，require用于从外部获取一个模块的接口，即所获取模块的exports对象。

![nodejs-require.jpg](https://upload-images.jianshu.io/upload_images/11297430-596438035d1350d2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Node.js 全局对象
* __filename表示当前正在执行的脚本的文件名。
* __dirname表示当前执行脚本所在的目录。
**process全局变量**

#### Node.js工具模块
OS模块：提供基本的系统操作函数。
Path模块：提供了处理和转换文件路径的工具。
Net模块：用于底层的网络通信。
DNS模块：用于解析域名。
Domain模块：简化异步代码的异常处理，可以捕捉处理try catch无法捕捉的。

#### Node.js Express框架
Expree框架核心特性：
 * 可以设置中间件来响应HTTP请求
 * 定义了路由表用于执行不同的HTTP请求动作
 * 可以通过向模版传递参数来动态渲染HTML页面

与express框架安装的重要模块
* body-parser：node.js中间件，用于处理JSON，Raw，Text和URL编码的数据。
* cookie-parser：解析Cookie的工具。
* multer：node.js中间件，用于处理enctype="multipart/form-data"(设置表单的MIME编码)的表单数据。
````
var express = require('express');
var app = express();

//Express提供了内置的中间件express.static来设置静态文件
app.use(express.static('public'));

//主页输出"Hello World"
app.get('/', function (req, res) {
  console.log('主页GET请求');
  res.send('Hello GET');
});

//POST请求
app.post('/', function(req, res) {
  console.log('主页POST请求');
  res.send('Hello POST');
});

//del_user页面响应
app.get('/del_user', function(req, res){
  console.log('/del_user响应DELETE请求');
  res.send('删除页面');
});

var server = app.listen(8081, function(){
  var host = server.address().address;
  var port = server.address().port;
  console.log('访问地址为http://%s:%s', host, port);
});
````
#### Node.js 多进程
每个子进程总是带有三个流对象：child.stdin, child.stdout和child.stderr。他们可能会共享父进程的stdio流，或者也可以是独立的被导流的流对象。
Node提供child_process模块来创建子进程，方法有：
  exec：使用子进程执行命令，缓存子进程的输出，并将子进程的输出以回调函数参数的形式返回。
  spawn：使用指定的命令行创建新进程。
  fork：是spawn的特殊形式，用于在子进程中运行的模块。与spawn不同的是，fork会在父进程和子进程之间，建立一个通信管道，用于进程之间的通信。

#### 代码链接
https://github.com/yxq199348/Node

#### 参考连接
http://www.runoob.com/nodejs/nodejs-tutorial.html