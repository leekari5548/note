### 文件上传接口返回HTTP状态码413

> 413对应Request Entity Too Large，请求实体过大。由于系统搭建了两个环境，一个直接连接tomcat容器，另外一个使用nginx服务器反向代理两个tomcat容器。直接使用tomcat的服务没有问题，则可以确认问题出现在nginx上。

       nginx服务器需要修改nginx.conf的请求报文大小的配置：
```
client_max_body_size 20M;
```
将client_max_body_size添加到http{ }、server{ }、location{}中的其中一个。http的作用域为全局，server的作用域为当前服务，location的作用域为当前路由。