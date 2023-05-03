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
