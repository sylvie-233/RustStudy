# Axum


## 基础介绍

异步高性能WEB框架


## 核心内容
```yaml
axum:
    extract: # 路由处理参数
        Multipart:
            next_field():
        Path:
        Query:
        Request: # 请求对象
            extensions(): 
            extensions_mut():
            method():
            uri():
        State: # 状态
    http:
        StatuCode:
    middleware:
        Next: # 放行函数
            run():
        from_fn():
        map_request(): 
        map_response(): 
    response:
        IntoResponse: # 自定义响应 trait
            into_response():
        Response: # 响应对象
            body():
            builder():
                body():
                header():
                status():
    routing: # 路由函数 
        get():
        post():
    Body:
    Json:
    Router: # 路由类
        fallback(): # 缺省路由
        layer(): # 路由层、中间件
        merge(): # 合并路由
        method_not_allowed_fallback():
        nest(): # 嵌套路由
        new():
        route(): # 挂载路由
        route_layer(): # 路由层、前置request、后置response拦截
        with_state():
    serve(): # 服务运行
    
tower_http: # 中间件库
    catch_panic:
        CatchPanicLayer:
    limit:
        RequestBodyLimitLayer:
    trace:
        TraceLayer:
            new_for_http():
```