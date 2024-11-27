# Rust

>
>``
>

## 基础介绍

rust程序：`.rs`文件

rust安装环境变量：`RUSTUP_HOME`、`CARGO_HOME`

rustup镜像环境变量：`RUSTUP_DIST_SERVER`、`RUSTUP_UPDATE_ROOT`


### rustup

rust工具链安装器

```yaml
rustup:
    check: # 检查工具更新
    component:
    doc: 打开本地文档
    default: 设置默认工具
    help:
    run:
    self: 修改已安装工具
        update:
        uninstall:
    show: 显示已安装的工具
    target:
    toolchain: 已安装的工具链
        install:
        list:
    update: # 更新rust工具
```


### rustc
```yaml
rustc:
    --version:
```

rust编译器





### cargo

rust包管理工具

```yaml
cargo:
    -h:
    --help:
    --version:
    add: # 添加第三方包
    bench: 跑测试
    build: 打包
        --release: 
    check: 检查代码
    clean:
    help:
    init: 初始化
    install:
    new: # 新建cargo包(项目)
    publish: 发布包
    remove: 移除包
    run: 运行
    uninstall:
    update: 更新包
```

cargo添加的依赖存放在`%CARGO_HOME%/registry`下



#### Cargo.toml
```yaml
package:
    authors:
    edition:
    name:
    version:
dependencies: 
```






## 核心内容
```yaml
std:
    __prelude:
        String:
        panic:
        println: # 打印(宏)
    cmp:
        Ordering:
            Equal:
            Great:
            Less:
    collections:
        HashMap:
            insert():
            new():
    fs:
    io:
        Result:
            expect(): # 打印异常细腻些
            is_ok():
            unwrap(): # 直接取结果
            Err():
            OK():
        Stdin:
            read_line():
        stdin(): # 获取输入流
    option:
        Option:
            None():
            Some():
    string:
        String:
            clone():
            cmp(): # 字符串比较
            from(): # 根据字符串常量创建字符串
            len():
            new(): # 新建字符串
            parse(): # 字符串解析
            push_str():
            trim():
    vec:
        Vec:
            append():
            new():

proc_macro:
    Group: # 代码段
    Ident: # 标识符
    Literal: # 字面量
    Punct: # 标点符号
    TokenStream:
        default():
        from():
        read_to_string():
    TokenTree:
rand:
    Rng:
        rand:
            thread_rng():
                get_range():
syn:
    ItemFn:
    parse_marco_input:

quote:
    quote: # 宏

```


### 数据类型
```yaml
type:
    bool:
    i32:
    i64:
    isize:
    u8:
    u32:
    u64:
    usize:
    f32:
    f64:
    char:
    str: 字符串切片
    Tuple: 元组
        0:
        1:
        2:
    Array: 数组
        [type; size]
        iter():
    Range: 范围
        rev():
    Slice: 切片
```


`let`定义的变量默认是不可修改的，加上`mut`才是可修改的，`const`定义常量

可以使用相同的名字声明新的变量，新的变量会shadow之前的同名变量
















#### String
```rust
pub struct String {
    vec: Vec<u8>,
}
```

![rust字符串内存模型](../assets/rust字符串内存模型.png)

String是str的指针，并拥有str的所有权，可以通过它修改str的值

`str`等效于`[u8]`

String与&str都是指向str的指针，String包含：指针、长度、容量，而&str只包含：指针、长度



#### Slice

`[T]`: 动态尺寸类型

切片不持有所有权，切片不一定代表引用

字符串切片的不可变引用`&str`：指向字符串一部分内容的引用

字符串字面值也是字符串切片


数组切片



#### Enum
```rust
enum Color {
    RED(type),
    BLUE(type)
}

Color::RED
```

枚举的每种字面量都可以定义不同类型（可利用enum实现类型别名），利于match解构和if let解构

枚举也可定义方法（impl）


#### Vector

堆上生成




### 控制流程

- match
- loop
- while
- for/ for in
- if let


Result解决了一部分异常处理的逻辑








#### match
```rust

```

模式匹配

match通常和枚举一块使用



#### 函数

`fn`定义函数

Statement语句最后一行的值默认为返回值



#### 异常处理





### Struct
```rust
pub struct User {
    id: u32,
    name: String
}

impl User {
    fn print(&self) {
        "实例方法定义"
    }

    fn new(id: u32, name: &str) {
        "静态方法定义"
    }
}
```

struct方法定义写在外面

struct结构：`..struct实例`

Tuple Struct
```rust
struct Color(i32, i32, i32);
```

struct赋值默认也是会发生移动Move的




#### trait

类似其它语言的接口













### Ownership


内存所有权，内存通过一个所有权系统来管理

栈内存、堆内存，使用所有权来管理heap上的数据

Copy trait、Drop trait

变量走出作用域时，会调用drop函数

引用`Reference`：&；引用传递不会丢失所有权，把引用作为函数参数的行为就叫做借用`Borrow`

`&mut`在特定作用域内，对某一块数据只能有一个可变引用；不可以同时拥有一个可变引用和一个不可变引用

`Danling Reference`悬空引用：编译器保证引用永远都不是悬空的


#### Move

移动：引用型变量赋值后会丢失所有权（默认发生移动）

栈上的数据不存在移动

函数返回堆上数据也会发生所有权一定给你


#### Lifetime

- &`static

变量生命周期，生命周期的主要作用是**避免悬垂引用**

生命周期标注通常是用在引用类型上的``&`a mut i32``


实际生命周期要大于等于声明的生命周期

在函数返回值有多个不同生命周期的的时候，要求返回类型是所有返回值中生命周期最小的那个

- 每一个引用参数都会获得独自的生命周期
- 若只有一个输入生命周期(函数参数中只有一个引用类型)，那么该生命周期会被赋给所有的输出生命周期，也就是所有返回值的生命周期都等于该输入生命周期

**struct自己的生命周期可以比属性引用的生命周期短**









### Smart Pointer




### Generic



### Module
```rust
mod mod_name {

}
```

Package->Crate->Module


模块默认是私有的，公共需标明`pub`

`use`使用模块中的东西，使用`as`定义别名


Crate类型：
- binary
- library


路径Path：绝对路径、相对路径（super、self）

默认隐式为根crate





### Attribute
```yaml
:
    allow:
        non_camel_case_types:
    cfg:
        条件编译
    cold:
    derive: 自动实现trait(可用于struct或枚举)
        Debug:
        Clone:
        Copy:
    feature:
        box_syntax:
    link:
        kind:
        name:
    macro_use:
    main: 主函数
    plugin_registrar:
    proc_macro: 定义宏函数
    proc_macro_attribute:
    should_panic:
    start:
    test:
```


Meta元数据表述：`#[name(arg1, arg2 = "param")]`



### Macro
```yaml
声明宏:
    assert_eq:
    include_str:
    panic:
    println:
    todo:
    vec:

过程宏:
    proc_macro_atttribute: 属性宏
```

![Rust编译过程](../assets/Rust编译过程.png)

Rust宏：声明宏、过程宏

自定义宏：`proc_macro`；tokenstream->string->tokenstream生成代码（元编程）

过程宏必须定义在一个单独的crate中

过程宏开发依赖包：
- proc-macro2：
- syn：
- quote：动态拼接字符串







### Test










### Concurrency


#### Async








### Unsafe







