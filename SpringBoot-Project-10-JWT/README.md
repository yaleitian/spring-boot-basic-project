# springboot-jwt

springboot中通过jwt进行用户认证的演示
参考博文:https://www.jianshu.com/p/e88d3f8151db  

## todo 据说有spring-security-jwt 有空研究下

## 主要依赖
```xml
<dependency>
    <groupId>com.auth0</groupId>
    <artifactId>java-jwt</artifactId>
    <version>3.10.3</version>
</dependency>
```

## 使用介绍

在yml中配置数据库,表格`user.sql`在/resources下  
生成玩数据库后启动项目

1. 第一次访问(GET) localhost:808/api/getMessage 时会显示
```json
{
    "message": "解析失败,请重新登陆"
}
```

2. 进行登陆(POST) localhost:8080/api/login?username=zhangsan&password=123456  
返回结果: 
```json
{
    "user": {
        "username": "zhangsan",
        "password": "123456",
        "id": "1"
    },
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJtc2ciOiJtZXNzYWdlIiwiYXVkIjoiMSIsInN1YiI6ImhlbGxvIHdvcmxkIiwiaXNzIjoiYWRtaW4iLCJleHAiOjE1OTExOTM4MTZ9.GkUY1m5eBUaXBs4bWrKSEAnz4wu7LRp86mamdtp_Isk"
}
```

3. 复制其中的`token`至header中(key:token,value:↑的token值),再次访问 localhost:8080/api/getMessage  
你可以看到`你已通过验证`(我设置jwt过期时间为5分钟)

详细关于jwt的配置可以在`JwtService`中看到

## 其他

java-jwt的github地址: https://github.com/auth0/java-jwt  
不明白的看官方guide是最好的选择