# tokio


## 基础介绍

rust异步运行时


## 核心内容
```yaml
tokio:
    fs:
        write():
    io:
        AsyncReadExt:
        AsyncWriteExt:
    net:
        TcpListener: # tcp监听器
    process:
    runtime:
    signal:
    stream:
    sync:
        mpsc:
            Receiver: # 通道接收者
                recv():
            Sender: # 通道发送者
                send():
            channel(): # 创建通道
        Mutex: # 互斥锁
            lock():
    task:
        spawn(): # 异步任务封装、并发运行多个任务
        spawn_blocking(): # 阻塞运行任务
    time:
        Duration:
            from_secs():
        sleep(): # 协程睡眠
        timeout(): # 超时
    @main: # attr
    @test: # test
    join!(): # 所有任务等待
    select!():
    spawn():
```