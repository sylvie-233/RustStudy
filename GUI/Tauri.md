# Tauri


## 基础介绍

webview GUI框架

### 项目结构
```yaml
项目结构:
    /public:
    /src:
    /src-tauri:
        /icons:
        /src:
            main.rs:
        /target:
        build.rs:
        Cargo.toml:
        tauri.conf.json:
    index.html:
    package.json:
    tsconfig.json:
    vite.config.ts:
```


#### tauri.conf.json
```yaml
tauri.conf.json:
    $schema:
    build:
    package:
    tauri:
        allowlist: # 权限设置
            all:
            fs:
            http: # api请求限制
                scope:
        bundle:
            resources:
        updater: # 软件更新
        windows:
```


## 核心内容
```yaml
tauri:
    @command: # 命令定义
    generate_context!():
    generate_handler![]:
    Builder:
        default():
        invoke_handler(): # command注册
        on_system_tray_event():
        run(): # 项目运行
        system_tray():
    CustomMenuItem:
    Manager:
    SystemTray:
        with_menu():
    SystemTrayEvent:
    SystemTrayMenu:
        add_item():
    Window: # 窗口
        emit(): # 事件触发
        get_window():

@tauri-apps:
    api:
        dialog:
            ask():
            confirm():
            open():
        event:
            listen():
        fs: # 文件操作
            BaseDirectory: # 文件目录路径预设
                Resource:
            readBinaryFile():
        http:
            fetch(): # request请求
        path:
            appDir():
            resourceDir():
            join():
        tauri:
            convertFileSrc():
            invoke(): # command调用
        window:
            appWindow:
                close():
                minimize():
            WebviewWindow:
                getByLabel():
                once():
```


### Command

命令


### Event

事件机制