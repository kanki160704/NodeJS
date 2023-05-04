# NodeJS 是一款运行js的软件
# Buffer: 类似数组，固定长度的字节序列
# 三种定义buffer的方法：
第一种时分配10字节，并且初始化为0
第二种分配字节时不会初始化
第三种buf3存储的是hello的内存
1. 
buf = Buffer.alloc(10)
console.log(buf)
2.
buf2 = Buffer.allocUnsafe(20)
console.log(buf2)
3.
buf3 = Buffer.from("hello")
console.log(buf3)

Buffer 转字符串 buf.toString()
查看buffer中单个元素 buf[1]，也可以进行修改
注意buffer中每一位最多储存到255

# fs 模块写入文件
这里err表示错误对象，如果有了错误就会存在
注意这里是异步操作，即写文件同时主线程会继续执行之后的代码，而io线程负责文件写入。
如果要同步操作，则使用 fs.writeFileSync("./a.txt", "aaa")，没有错误对象部分
追加写入使用 appendFile 和 appendFileSync
```
var fs = require("fs")
fs.writeFile("./a.txt", "aaa", err => {
    if (err) {
        console.log("fail")
    }
    else {
        console.log("success")
    }
})
```

# fs 模块流式写入
适合写入较大文件
```
var fs = require("fs")
var ws = fs.createWriteStream("./a.txt")
ws.write("aaa\r\n")
ws.write("bbb")
ws.close()
```

# fs 异步读取
同步读取类似同步写入
```
var fs = require("fs")
fs.readFile("./a.txt", (err, data)=> {
    if (err) {
        console.log("error")
        return
    }
    console.log(data.toString())
})
```

# fs 流式读取
可以绑定读取到内容后事件，读取完成后事件等
```
var fs = require("fs")
var rs = fs.createReadStream("./a.txt")
rs.on("data", chunk => {
    console.log(chunk.toString())
})
rs.on("end", ()=>{
    console.log("end")
})
```

# 获取绝对路径
```
var fs = require("fs")
var path = require("path")
var p = path.resolve(__dirname, './index.html')
console.log(p)
```

# http 包
以下内容可以生成一个监听本机9000端口的服务器，end函数可以定义请求体内容
```
var http = require("http")
var server = http.createServer((request, response)=> {
    response.end("aaa")
})

server.listen(9000, ()=> {
    console.log("start")
})
```
