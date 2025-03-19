# Rocket

`Rust-Rocket框架：P24`

## 基础介绍


rust Web框架


### Rocket.toml
```yaml
default:
    
```

rocket配置文件





## 核心内容
```yaml
rocket:
    data:
        Data:
            open():
            stream_to():
        FromData:
        ToByteUnit:
    fs:
        NamedFile:
            open():
        TempFile: # 临时文件
            persist_to:
    http:
        ContentType:
            JSON:
        Cookie:
            named():
        CookieJar:
            get():
            get_private():
            remove_private():
        Status:
    io:
        stdout():
    request:
        FromRequest: # 请求守卫，trait
            from_request():
        Outcome:
        Request:
    response:
        content:
            RawJson:
        status:
            Accepted:
            Custom:
        Flash:
            success():
        Redirecto:
            to():
        Response:
            build():
            header():
            ok():
            sized_body():
    serde:
        json:
            Json:
        @Deserialize:
    tokio:
        task:
        time:
            Duration:
            sleep():
    @async_trait:
    @catch: # 异常处理
    @get:
        rank:
    @launch:
    @post:
        data:
        format:
    @Responder:
    @response:
    catchers![]:
    routes![]: # 路由列表
    uri!():
    Config:
        address:
        port:
        temp_dir:
    Data:
    Error:
    Request: # 请求对象
        headers():
        uri():
    Response: # 响应对象
    Rocket: # 应用对象
        attach():
        config():
        launch():
        manage():
        mount(): # 路由挂载
        register(): # 注册异常处理函数
        shutdown():
    Route:
    State: # 状态值
    build():
rocket_db_pools:
    sqlx:
        query!():
            fetch_one():
        MySqlPool:
    @database:
    @Database:
    Connection:
    Pool:
rocket_dyn_templates:
    context!{}: # 模板数据
    Template: # 页面模板
        fairing():
        render():
```