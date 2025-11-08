# Rust

>
>`Rust官方API文档：https://doc.rust-lang.org/std/index.html`
>`Rust官方文档：https://doc.rust-lang.org/book/`
>
>`Rust 编程语言教程 with RustRover：29`

## 基础介绍

编译型、无GC、安全性高的系统编程语言
- Option可空处理
- Result异常处理
- Future异步
- Box智能指针


rust程序：`.rs`文件

rust安装环境变量：`RUSTUP_HOME`、`CARGO_HOME`
- `RUSTUP_HOME`: Rust编译工具链
- `CARGO_HOME`:  Cargo包管理主目录
rustup镜像环境变量：`RUSTUP_DIST_SERVER`、`RUSTUP_UPDATE_ROOT`

要求写分号`;`
变量支持自动类型推断、默认不可变

- cargo添加的依赖存放在`%CARGO_HOME%/registry`下



### rustup
```yaml
rustup:
    check: # 检查工具更新
    component: # 功能组件管理
        add:
            rustfmt:
    doc: # 打开本地文档
    default: # 设置默认工具(rust版本管理)
        nightly:
        stable:
    help:
    run:
    self: # 修改已安装工具
        update:
        uninstall: # 卸载rust
    show: # 显示已安装的工具
    target:
    toolchain: # 已安装的工具链
        install:
        list:
    update: # 更新rust工具
```

rust工具链安装器


### rustc
```yaml
rustc:
    -o:
    --crate-type:
        lib:
    --version:
```

rust编译器





### cargo
```yaml
cargo:
    -h:
    --help:
    --version:
    add: # 添加第三方包
        --build:
        --dev:
    bench: # 测试
    build: # 打包
        --release: 
    check: # 检查代码
    clean:
    help:
    init: # 初始化
    install: # 打包到本地仓库
    new: # 新建cargo包(项目)
        --lib:
    publish: # 发布包
    remove: # 移除包
    run: # 运行
    test: # 运行测试代码
    uninstall:
    update: # 更新包
```

rust包管理工具





#### Cargo.toml
```yaml
build-dependencies:
dependencies: 
dev-dependencies:
package:
    authors:
    edition:
    name:
    version:
```






## 核心内容
```yaml
alloc:
core:
proc_macro: # 过程宏
    token_stream:
    Group: # 代码段
    Ident: # 标识符
    Literal: # 字面量
    Punct: # 标点符号
    TokenStream:
        default():
        from():
        read_to_string():
    TokenTree:
std: # 核心包
    alloc:
    any:
    array: # 固定大小数组
        chunks(): # 分块
        into_iter():
        iter(): # 显式迭代器
        len(): # 长度
        split():
        windows(): # 滑动窗口
    boxed:
        Box: # 智能指针
    cell:
    clone:
        Clone:
    cmp: # 比较
        Eq:
        Ord:
        Ordering:
            Equal:
            Great:
            Less:
        PartialEq:
        PartialOrd:
    collections: # 集合
        BinaryHeap:
        BTreeMap:
        BTreeSet:
        HashMap: # 哈希表
            contains_key(): # k 存在判断
            entry():
            get(): # 获取元素，Option
            insert(): # 添加元素
            iter(): # k-v迭代，元组
            len(): # 元素个数
            new():
            remove(): # 移除元素，Option
        HashSet: # 集合
            contains():
            get():
            insert():
            iter():
            len():
            new():
        LinkedList:
        VecDeque:
    convert: # 转换
        AsRef:
        AsMut:
        Into:
        From:
    default:
        Default:
    env: # 环境
        args(): # 命令行参数
    error:
        Error:
    fmt: # 格式化
        Display: # 自定义控制台输出 trait
            fmt():
        format(): # 字符串格式化
    fs: # 文件
        DirEntry: # 文件条目
            file_name():
            file_type():
            metadata():
            path():
        File: # 文件
            create(): # 创建文件
            open(): # 打开文件
            read_to_string(): # 字符串读取
            write(): # 文件写入
            write_all():
        FileType: # 文件类型
            file_type():
            is_dir():
            is_file():
        Metadata: # 文件元信息
            is_dir():
            is_file():
            len(): # 文件大小
        OpenOptions: # 文件打开配置
            append(): # 文件追加选项
            new():
            open(): # 打开文件：File
        Permissions:
        ReadDir: # 
        copy(): # 文件拷贝
        create_dir(): # 创建目录
        create_dir_all():
        metadata(): # 获取文件元信息
        read(): # 读取字节数据: Vec<u8>
        read_dir(): # 读取目录，迭代遍历 DirEntry
        read_to_string(): # 读取文件内容
        remove_dir():
        remove_file(): # 删除文件
        rename(): # 重命名
        write(): # 文件写入
    future: # 异步结果
        Future: # 异步结果
            poll(): # await 简化操作
    hash: # 哈希
        Hash:
        Hasher:
    io: # 输入输出
        BufReader: # 缓冲输入
            lines(): # 获取所有行
            new():
            read_line():
        BufWriter: # 缓存输出
        Bytes:
        Read: # 输入流 trait
        Result:
            expect(): # 打印异常细腻些
            is_ok():
            unwrap(): # 直接取结果
            Err():
            OK():
        Stdin: # 标准输入流
            lock():
            read_line(): # 读取一行
        Stdout: # 标准输出流 
            write():
        Write: # 输出流 trait
            write_all():
        stdin(): # 获取输入流
    iter: # 迭代器
        DoubleEndedIterator:
        ExactSizeIterator:
        Extend:
        IntoIterator: 
        Iterator:
    marker:
        Copy:
        Send:
        Sized:
        Sync:
        Unpin:
    mem: # 内存
        align_of():
        align_of_val():
        drop():
        sizeof(): # 内存大小
        size_of_val(): # 变量内存大小
    net: # 网络
        IpAddr:
            V4:
        TcpListener:
            bind():
            incoming():
        TcpStream:
            connect():
            read():
            write():
        UdpSocket:
            bind():
            recv_from():
            send_to():
    ops: # 操作定义
        Deref: # 只读智能指针，*v
        Drop: # 析构，Trait，Move
        Fn: # 函数
        FnMut: #
        AsyncFn:
        AsyncFnMut:
        AsyncFnOnce:
        Drop:
        Fn:
        FnMut:
        FnOnce:
        Range: # 范围
            end:
            start:
            contains(): # 值包含
            enumerate(): # 带索引遍历
            is_empty():
            step_by(): # 步长
        RangeFrom:
        RangeInclusive:
        RangeTo:
        RangeToInclusive:
    option: # 可空
        Option: # 可空枚举
            None:
            Some: # 有值
            and():
            and_then():
            as_ref(): # 获取引用
            expect():
            get_or_insert():
            get_or_insert_default():
            insert():
            is_none():
            is_none_or():
            is_some():
            is_some_or():
            map():
            map_or():
            map_or_else():
            ok_or():
            ok_or_else():
            or():
            or_else():
            replace():
            take():
            unwrap():
            unwrap_or():
            unwrap_or_default():
            unwrap_or_else():
    os: # 操作系统
    path: # 路径
        Path:
            join():
            new():
        PathBuf:
    prelude: # 预加载模块
    process: # 进程
    result: # 结果
        Result: # 结果枚举、异常处理
            Err:
            Ok:
            and():
            and_then():
            err():
            expect(): # 抛出异常信息
            expect_err():
            is_err():
            is_err_and():
            is_ok():
    slice: # 切片
    str: # 不可变字符串、字符串切片
        as_bytes(): # 转为字节数组 &[u8]
        char_indices():
        chars():
        len():
        parse():
        split():
        to_string(): # 转换为字符串
        trim():
    string: # 字符串
        String: # 可变字符串(引用类型)
            as_str():
            bytes(): # 转换为字节数组
            chars(): # 转换为字符数组
            clone():
            cmp(): # 字符串比较
            from(): # 根据字符串常量创建字符串
            from_utf8_lossy():
            len(): # 字符串长度
            new(): # 新建字符串
            parse(): # 字符串解析
            push(): # 添加字符
            push_str(): # 添加字符串
            trim():
    sync: # 同步
        atomic:
            AtomicUsize:
            Ordering:
        Arc:
        Mutex:
            lock():
    task: # 任务
        Poll:
            Pending:
            Ready:
    thread: # 线程
        JoinHandle: # 线程操作
            is_finished():
            join():
            thread():
        Thread: # 线程
            id():
            name():
        sleep(): # 线程睡眠
        spawn(): # 开启线程
    time:
    vec: # 动态数组
        Vec: # 动态数组
            capacity():
            clone(): # 拷贝
            contains(): # 元素包含判断
            into_iter():
            len(): # 长度
            new():
            pop():
            push(): # 添加元素
            remove(): # 根据索引移除元素
            with_capacity():
    format!(): # 字符串格式化：String
    panic!(): # 异常抛出(宏)，不可恢复
    print!():
    println!(): # 打印输出(宏)、支持字符串格式化
    vec![]: # 创建Vec
    write!():
    writeln!():
test: # 测试库
```


### Data Types
```yaml
DataTypes:
    array: # 数组类型
    bool: # 布尔
    char: # 字符（4字节）
    f32:
    f64: # 浮点数、默认
    fn: # 函数
    i32: # 整形、默认
    i64:
    isize:
    pointer: # 指针
    reference: # 引用
    slice: # 切片
    str: # 字符串切片
    tuple: # 元组
        .0:
        .1:
        .2:
    u8: # 字节
    u32:
    u64:
    unit: # 空类型
    usize:
```

`let`:
`let mut`:
`const`: 定义常量
`static`: 静态变量

变量默认是不可修改的
可以使用相同的名字声明新的变量，新的变量会shadow之前的同名变量
const声明不允许重复声明








#### str
```rust
// 字符串字面量
let s: &str = "Hello, Rust!";

// 多行字符串
let s = r#"
    多行字符串
"#
```

&str 是不可变的字符串切片，是对 String 或字面量字符串的引用
Copy

字符串切片的不可变引用`&str`：指向字符串一部分内容的引用
字符串字面值也是字符串切片



#### String
```rust
// 根据字面量创建
let mut s = String::from("Hello");
```

可变字符串
Move


String 是可变的、拥有所有权的字符串类型，通常用于动态构建和修改字符串

String是str的指针，并拥有str的所有权，可以通过它修改str的值
`str`等效于`[u8]`
String与&str都是指向str的指针，String包含：指针、长度、容量，而&str只包含：指针、长度

![rust字符串内存模型](../assets/rust字符串内存模型.png)


#### Array
```rust
// 字面量声明
let arr: [i32; 4] = [1, 2, 3, 4];

// 重复初始化
let arr = [0; 5]; // 等价于 [0, 0, 0, 0, 0]
```

固定长度数组、Copy 
`[T; N]`

支持索引、for in遍历、


#### Tuple
```rust
// 字面量创建
let tup: (i32, f64, char) = (42, 3.14, 'R');

tup.0
tup.1
tup.2
```

元组、Copy

支持下标索引(0,1,2)、解构
空元组 ()




#### Range
```rust
// for 循环遍历
for i in 1..5 {
    println!("{}", i); // 输出 1 2 3 4
}
```


范围
Copy

`..`左闭右开、`..=`左右闭合
支持for in 遍历、





#### Slice
```rust
// 字符串切片
let s = String::from("Hello, Rust!");
let slice: &str = &s[0..5]; // 取前 5 个字符

// 数组切片
let arr = [10, 20, 30, 40, 50];
let slice: &[i32] = &arr[1..4]; // 取索引 1 到 3（左闭右开）

```

`&T`、`&mut T`：借用、可变借用
Copy
左闭右开
切片、可变切片


切片 (slice) 是对数组或 Vec 的一部分的引用，用于避免复制数据，提高性能
切片不持有所有权







#### Vec
```rust
// 宏声明
let v = vec![1, 2, 3]; // `v` 存在栈上，但元素 [1,2,3] 存在堆上

```

动态数组、Move

支持索引、for in遍历


#### HashMap


哈希表

引用类型Move


#### HashSet


#### Enum
```rust
enum Color {
    RED(type),
    BLUE(type)
}

Color::RED
```

枚举

利于match解构和if let解构
枚举也可定义方法impl



### Control Flow
```yaml
ControlFlow:
    as: # 强制类型转换
    const: # 常量定义
    let: # 变量定义
    macro_rules!: # 声明宏定义
    mut: # 可变定义
    ref: # 引用&
    static: # 静态变量
    type: # 类型别名
    where: # 泛型限定
    for ... in ...: # 迭代遍历
    if ... else if ... else ...:
    loop ...:
    match ...:
    unsafe ...: 
    while ...:
        break:
        continue:
```

Result解决了一部分异常处理的逻辑








#### Match
```rust
match number {
    1 | 2 => println!("One or Two!"),
    3 => println!("Three!"),
    _ => println!("Other number!"),
}
```

模式匹配

match通常和枚举(Option、Result)一块使用
支持解构、匹配守卫（if 条件）、



#### Option

可空处理


#### Exception Handle

异常处理
`Result`

##### Result

`?`运算符

##### Panic





### Function



`fn`定义函数

Statement语句最后一行的值默认为返回值

不支持可变参数

#### Closure
```rust
let add = |a: i32, b: i32| a + b; // 定义一个闭包
println!("5 + 3 = {}", add(5, 3));
```

函数闭包



#### Generic


泛型
where泛型限定


#### Async


异步函数



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

结构体
- 如果struct里只包含拥有所有权的字段，那么它是值类型。
- struct包含引用时，变成引用类型

结构体默认是不可变的
struct赋值默认也是会发生移动Move的
struct方法定义写在外面impl

支持解构


#### Tuple Struct
```rust
struct Color(i32, i32, i32);
```

元组结构体、类似kotlin的data class


#### Unit Struct

单元结构体、无实体结构体，仅用于标记


#### Trait
```rust
// 定义一个 trait
trait Speak {
    fn speak(&self);  // 定义一个方法，所有实现此 trait 的类型都需要提供这个方法的实现
}

// 为结构体实现 trait
struct Person {
    name: String,
}

impl Speak for Person {
    fn speak(&self) {
        println!("Hello, my name is {}", self.name);
    }
}

// Trait继承
trait Animal {
    fn sound(&self);
}

trait CanFly {
    fn fly(&self);
}

trait Bird: Animal + CanFly {  // Bird 继承自 Animal 和 CanFly
    fn chirp(&self);
}
```
特质、类似其它语言的接口


常用于泛型约束、实现结构体的魔术方法
支持默认实现、


##### AsMut
##### AsRef

##### Clone

复制

##### Copy

拷贝


##### Debug

调试输出

##### Deref
##### DerefMut

##### Drop

析构

##### Default

默认值


##### Display


字符串打印


##### Eq

相等判断

##### From

类型转换

##### Into

类型转换

##### IntoIterator

for in 迭代遍历


##### Iterator

迭代器

##### Ord

排序

##### Sized



#### Generic

泛型





### Ownership


内存所有权，内存通过一个所有权系统来管理

栈内存、堆内存，使用所有权来管理heap上的数据

Copy trait、Drop trait

变量走出作用域时，会调用drop函数

引用`Reference`&；引用传递不会丢失所有权，把引用作为函数参数的行为就叫做借用`Borrow`

`&mut`在特定作用域内，对某一块数据只能有一个可变引用；不可以同时拥有一个可变引用和一个不可变引用

`Danling Reference`悬空引用：编译器保证引用永远都不是悬空的



#### Borrow


借用，不会发生Move
不可变借用`&`、可变借用`&mut`



#### Move

移动：引用型变量赋值后会丢失所有权（默认发生移动）
- 赋值时发生Move
- 函数传参时发生Move
- 函数返回值会Move
- Option<T>或Some(T)解构发生Move


栈上的数据不存在移动

函数返回堆上数据也会发生所有权移动给你


#### Lifetime
```rust
// 函数生命周期
fn longest<'a>(s1: &'a str, s2: &'a str) -> &'a str {
    if s1.len() > s2.len() {
        s1
    } else {
        s2
    }
}

// 结构体生命周期
struct Book<'a> {
    title: &'a str,
    author: &'a str,
}
```


生命周期、避免悬垂指针

生命周期描述了引用有效的范围，也就是一个引用从创建到销毁的时间跨度。Rust 编译器会在编译时检查引用是否遵循生命周期规则，确保引用的数据不会在引用之前被销毁
- 每个引用都有一个生命周期，表示引用有效的范围。
- Rust编译器会根据变量的作用域自动推断生命周期，通常我们不需要显式指定生命周期


需要手动标注的情况：
- 返回值是引用，且参数中有多个引用
- 结构体持有引用，当struct有生命周期时，impl也必须声明

只有一个引用参数，Rust 自动推导生命周期，不需要手动标注的情况




#### Smart Pointer




##### Box

单所有权，堆分配


##### Arc
##### Rc
```rust
let a = Rc::new(5);
let b = Rc::clone(&a);

println!("a: {}, b: {}", a, b);
```

共享所有权，引用计数

##### RefCell
```rust
let x = RefCell::new(5);
    
let mut y = x.borrow_mut();
*y += 1;
    
println!("Value: {}", x.borrow());
```

内部可变性的智能指针，它们使得你能够在不改变所有权的情况下修改数据

##### Mutex

##### Cow
```rust
```

写时复制，优化不需要修改的数据





### Module
```rust
mod mod_name {

}
```

Package->Crate->Module

`mod.rs`默认模块文件
模块默认是私有的，公共需标明`pub`

`use`使用模块中的东西，使用`as`定义别名


Crate类型：
- binary
- library

路径Path：
- 绝对路径
- 相对路径super、self

模块默认是私有的，公共需标明`pub`
`use`使用模块中的东西，使用`as`定义别名
默认隐式为根crate





### Attribute
```yaml
Attribute:
    allow:
        non_camel_case_types:
    cfg: # 条件编译
    cold:
    derive: 自动实现trait(可用于struct或枚举)
        Debug:
        Clone:
        Copy:
        Debug:
        PartialEq:
    feature:
        box_syntax:
    inline: # 函数内联
        always:
    link:
        kind:
        name:
    macro_use: # 引入crate模块中的宏
    main: # 主函数
    must_use:
    no_mangle:
    non_exhaustive:
    panic_handler:
    plugin_registrar:
    proc_macro: # 定义宏函数
    proc_macro_attribute:
    repr: # 内存布局控制
    should_panic:
    start:
    test: # 测试函数标记
    unstable:
    warn:
```

注解元数据
`#[attr]`




### Macro
```yaml
macro:
```

![Rust编译过程](../assets/Rust编译过程.png)

Rust宏：
- 声明宏: 类似原始c++宏
- 过程宏: 自定义代码token流处理
    - 派生宏: 自动为结构体或枚举生成trait实现
    - 属性宏: 可以用于自定义属性
    - 函数宏:



#### Declarative Macro
```rust
// 简单宏
macro_rules! say_hello {
    () => {
        println!("Hello, World!");
    };
}

say_hello!();  // 调用宏


// 带参数宏
macro_rules! create_point {
    ($x:expr, $y:expr) => {
        ( $x, $y )
    };
}

let point = create_point!(1, 2);


// 可变参数宏
macro_rules! test {
    ($val:expr) => {
        println!("Evaluating value: {}", $val);
    };
    ($val:expr, $msg:expr) => {
        println!("{}: {}", $msg, $val);
    };
}
```


声明式宏是通过 macro_rules! 关键字来定义的。它允许你定义规则来匹配特定的模式，并生成代码


#### Procedural Macro


##### Derive Macro
```rust
// 自定义派生宏，为struct生成trait实现
use proc_macro::TokenStream;

#[proc_macro_derive(HelloWorld)]
pub fn hello_world_macro(input: TokenStream) -> TokenStream {
    let _input = input.to_string(); // 获取输入代码作为字符串
    "impl HelloWorld for TestStruct { fn hello() { println!(\"Hello, World!\"); } }".parse().unwrap()
}

// 使用自定义派生宏
#[derive(HelloWorld)]
struct TestStruct;
```




##### Attribute Macro
```rust
#[proc_macro_attribute]
pub fn my_attribute(attr: TokenStream, item: TokenStream) -> TokenStream {
    // 处理属性和代码
    println!("Attribute: {}", attr); //foo
    println!("Item: {}", item); // my_function
    item
}

// 调用自定义属性宏
#[my_attribute(foo)]
fn my_function() {
    println!("Hello from function!");
}
```


属性宏允许你为函数、结构体、模块等自定义属性处理


##### Function Macro
```rust
#[proc_macro]
pub fn my_macro(input: TokenStream) -> TokenStream {
    let input_str = input.to_string();  // 获取输入的字符串
    let output = format!("println!(\"{}\");", input_str);  // 生成代码
    output.parse().unwrap()
}

// 调用自定义函数宏
my_macro!(Hello, World!);
```







### Test

测试
`#[cfg(test)]`、`#[test]`








### Concurrency









### Unsafe







