
# Windows下IE浏览器文件下载

微软系浏览器的内核特立独行，下载文件的文件名编码格式不同于其他浏览器，经常会造成乱码的问题。通过`HttpServletRequest`获取到对应的`User-Agent`来判断浏览器的类型。如下为chrome浏览器在MacOS下的User-Agent。

```
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.125 Safari/537.36
```

IE10(包含IE10)以下的User-Agent都比较接近，都统一包含MSIE，只是其版本不一致。

```
Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)    //IE8
Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Trident/5.0)   //IE9
Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)  //IE10
```

而IE11不同，MSIE从IE11的User-Agent中消失了，可以通过Trident来判断。

```
Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; .NET4.0C; .NET4.0E; rv:11.0) like Gecko
```

直接下载文件时会将文件名写入请求头，而此时，IE浏览器就会出现下载的文件名乱码的问题。

```java
response.setHeader("Content-Disposition", "attachment;fileName=" + filename);
```

为了解决IE下载文件文件名乱码的错误，通过上述的User-Agent来判断是否为IE浏览器，如果为IE浏览器，则对文件名字进行`URLEncoder.encode(filename, "utf-8")`处理。

```java
//解决ie下载时文件名乱码的问题
public static String getDownloadFileName(String filename, final HttpServletRequest request){
  	String agent = request.getHeader("User-Agent").toUpperCase();
		String realName = null;
		
  	//判断是否是ie浏览器
		if (agent.contains("MSIE") || agent.contains("TRIDENT")) {   
			realName = URLEncoder.encode(filename, "utf-8");
		}else{
			realName = new String(filename.getBytes(), StandardCharsets.ISO_8859_1);
		}
		return realName;
}
```

此外，在IE浏览器中下载压缩文件时，解压缩后的文件名也会出现乱码现象。

```java
ZipOutputStream zos = new ZipOutputStream(response.getOutputStream());
```

通过查看源码，可以发现`ZipOutputStream`的构造方法默认使用`UTF-8`格式。

```java
/**
 * Creates a new ZIP output stream.
 *
 * <p>The UTF-8 {@link java.nio.charset.Charset charset} is used
 * to encode the entry names and comments.
 *
 * @param out the actual output stream
 */
public ZipOutputStream(OutputStream out) {
  	this(out, StandardCharsets.UTF_8);
}
```

而IE浏览器下对中文的编码默认为`GBK`，此时需要针对于IE指定特定格式的编码GBK。

```java
ZipOutputStream zos = new ZipOutputStream(response.getOutputStream(), Charset.forName("GBK"));
```

此时下载的文件解压之后就不会有乱码的现象。


