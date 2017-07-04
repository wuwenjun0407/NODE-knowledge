# node 内置模块用法
###  node 内置模块用法

```
let http=require("http");
let url=require("url");
let fs=require("fs");
http.createServer((req,res)=>{
    let{pathname,query}=url.parse(req.url);
    let pathReg=/\.([0-9a-zA-Z]+)$/i;
    if(pathReg.test(pathname)){
        let readF=null,
            status=200;
        try {
            readF=fs.readdirSync("."+pathname);
        }catch (e){
            console.log("not fond");
            status=404;
        }
        //通过路径信息获取MIME类型
        let suffix=pathReg.exec(pathname)[1].toUpperCase();
        let suffixMIME="text/plain";
        switch (suffix){
            case "HTML":
                suffixMIME="text/html";
                break;
            case "JS":
                suffixMIME="text/javascript";
                break;
            case "CSS":
                suffixMIME="text/css";
                break;
            case "PNG":
                suffixMIME="image/png";
                break;
            case "JPG":
                suffixMIME="image/jpg";
                break;
            case "GIF":
                suffixMIME="image/gif";
                break;
            case "JPEG":
                suffixMIME="image/jpeg";
                break;
        }
        //overWrite response header
        res.writeHead(status,{
            "content-type":suffixMIME+";charset=utf-8"
        });
    }
    res.end("The requested file is not a resource file")
}).listen(4321,()=>{
    console.log("OK")
});
    
```

### body-parser第三方模块用法
```
var express=require("express"),
    bodyParser=require("body-parser"),
    fs=require("fs");
var app=express();//就相当于创建一个服务
//处理资源文件请求
app.use(express.static(__dirname));
//处理数据请求
app.use(bodyParser.json());
//监听一个端口
app.listen(1234,()=>{
    console.log("1234 OK!")
});
//如果你请求的是根目录，也就是说地址是http://localhost:1234/
app.get("/",(request,response)=>{
    response.sendFile("./messageBoard.html",{root:__dirname})
});
//创建一个数组来存放发送过来的留言对象
var messageAry=JSON.parse(fs.readFileSync("./json/messageData.json","utf-8"));
app.post("/messageTop",(request,response)=>{
    //request.body就是客户端传进来的参数 直接就是一个对象
    if(request.body.title||request.body.content){
        messageAry.push(request.body);
    }
    fs.writeFileSync("./json/messageData.json",JSON.stringify(messageAry));
    response.send(fs.readFileSync("./json/messageData.json","utf-8"));
});
```