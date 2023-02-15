# Go语法学习

## 语言结构

- 包声明
- 引入包
- 函数
- 变量
- 语句 & 表达式
- 注释

## 关键字

下面列举了 Go 代码中会使用到的 25 个关键字或保留字：

|          |             |        |           |        |
| -------- | ----------- | ------ | --------- | ------ |
| break    | default     | func   | interface | select |
| case     | defer       | go     | map       | struct |
| chan     | else        | goto   | package   | switch |
| const    | fallthrough | if     | range     | type   |
| continue | for         | import | return    | var    |

除了以上介绍的这些关键字，Go 语言还有 36 个预定义标识符：

|        |         |         |         |        |         |           |            |         |
| ------ | ------- | ------- | ------- | ------ | ------- | --------- | ---------- | ------- |
| append | bool    | byte    | cap     | close  | complex | complex64 | complex128 | uint16  |
| copy   | false   | float32 | float64 | imag   | int     | int8      | int16      | uint32  |
| int32  | int64   | iota    | len     | make   | new     | nil       | panic      | uint64  |
| print  | println | real    | recover | string | true    | uint      | uint8      | uintptr |

程序一般由关键字、常量、变量、运算符、类型和函数组成。

程序中可能会使用到这些分隔符：括号 ()，中括号 [] 和大括号 {}。

程序中可能会使用到这些标点符号：.、,、;、: 和 …。

## 类型-数据

数据类型的出现是为了把数据分成所需内存大小不同的数据，编程的时候需要用大数据的时候才需要申请大内存，就可以充分利用内存。

Go 语言按类别有以下几种数据类型：

| 序号  | 类型和描述                                                                                                                                                                 |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **布尔型**<br>布尔型的值只可以是常量 true 或者 false。一个简单的例子：var b bool = true。                                                                                                       |
| 2   | **数字类型**<br>整型 int 和浮点型 float32、float64，Go 语言支持整型和浮点型数字，并且支持复数，其中位的运算采用补码。                                                                                            |
| 3   | **字符串类型:**<br>字符串就是一串固定长度的字符连接起来的字符序列。Go 的字符串是由单个字节连接起来的。Go 语言的字符串的字节使用 UTF-8 编码标识 Unicode 文本。                                                                        |
| 4   | **派生类型:**<br>包括：<br>- (a) 指针类型（Pointer）<br>- (b) 数组类型<br>- (c) 结构化类型(struct)<br>- (d) Channel 类型<br>- (e) 函数类型<br>- (f) 切片类型<br>- (g) 接口类型（interface）<br>- (h) Map 类型 |

## 数字类型

Go 也有基于架构的类型，例如：int、uint 和 uintptr。

| 序号  | 类型和描述                                                                |
| --- | -------------------------------------------------------------------- |
| 1   | **uint8**<br>无符号 8 位整型 (0 到 255)                                     |
| 2   | **uint16**<br>无符号 16 位整型 (0 到 65535)                                 |
| 3   | **uint32**<br>无符号 32 位整型 (0 到 4294967295)                            |
| 4   | **uint64**<br>无符号 64 位整型 (0 到 18446744073709551615)                  |
| 5   | **int8**<br>有符号 8 位整型 (-128 到 127)                                   |
| 6   | **int16**<br>有符号 16 位整型 (-32768 到 32767)                             |
| 7   | **int32**<br>有符号 32 位整型 (-2147483648 到 2147483647)                   |
| 8   | **int64**<br>有符号 64 位整型 (-9223372036854775808 到 9223372036854775807) |

### 浮点型

| 序号  | 类型和描述                           |
| --- | ------------------------------- |
| 1   | **float32**<br>IEEE-754 32位浮点型数 |
| 2   | **float64**<br>IEEE-754 64位浮点型数 |
| 3   | **complex64**<br>32 位实数和虚数      |
| 4   | **complex128**<br>64 位实数和虚数     |

---

### 其他数字类型

以下列出了其他更多的数字类型：

| 序号  | 类型和描述                         |
| --- | ----------------------------- |
| 1   | **byte**<br>类似 uint8          |
| 2   | **rune**<br>类似 int32          |
| 3   | **uint**<br>32 或 64 位         |
| 4   | **int**<br>与 uint 一样大小        |
| 5   | **uintptr**<br>无符号整型，用于存放一个指针 |

## 类型-数组

### 声明数组

Go 语言数组声明需要指定元素类型及元素个数，语法格式如下：

```go
var variable_name [SIZE] variable_type
```

以上为一维数组的定义方式。例如以下定义了数组 balance 长度为 10 类型为 float32：

```go
var balance [10] float32
```

### 初始化数组

以下演示了数组初始化：

```
var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

我们也可以通过字面量在声明数组的同时快速初始化数组：

```
balance := [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

如果数组长度不确定，可以使用 ... 代替数组的长度，编译器会根据元素个数自行推断数组的长度：

```
var balance = [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
或
balance := [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

如果设置了数组的长度，我们还可以通过指定下标来初始化元素：

```
//  将索引为 1 和 3 的元素初始化
balance := [5]float32{1:2.0,3:7.0}
```

初始化数组中 {} 中的元素个数不能大于 [] 中的数字。

## 类型-指针

### 如何使用指针

指针使用流程：

- 定义指针变量。
- 为指针变量赋值。
- 访问指针变量中指向地址的值。

```go
package main

import "fmt"

func main() {
   var a int= 20   /* 声明实际变量 */
   var ip *int        /* 声明指针变量 */

   ip = &a  /* 指针变量的存储地址 */

   fmt.Printf("a 变量的地址是: %x\n", &a  )

   /* 指针变量的存储地址 */
   fmt.Printf("ip 变量储存的指针地址: %x\n", ip )

   /* 使用指针访问值 */
   fmt.Printf("*ip 变量的值: %d\n", *ip )
}
```

## 类型-结构体

### 定义结构体

结构体定义需要使用 type 和 struct 语句。struct 语句定义一个新的数据类型，结构体中有一个或多个成员。type 语句设定了结构体的名称。结构体的格式如下：

```
type struct_variable_type struct {
   member definition
   member definition   ...
   member definition
}
```

一旦定义了结构体类型，它就能用于变量的声明，语法格式如下：

```
variable_name := structure_variable_type {value1, value2...valuen}
或
variable_name := structure_variable_type { key1: value1, key2: value2..., keyn: valuen}
```

### 访问结构体成员

如果要访问结构体成员，需要使用点号 . 操作符，格式为：

```go
结构体.成员名
```

## 类型-切片

Go 数组的长度不可改变，在特定场景中这样的集合就不太适用，Go 中提供了一种灵活，功能强悍的内置类型切片("动态数组")，与数组相比切片的长度是不固定的，可以追加元素，在追加时可能使切片的容量增大。

## 类型-Map

#### 定义 Map

可以使用内建函数 make 或使用 map 关键字来定义 Map:

```
/* 使用 make 函数 */
map_variable := make(map[KeyType]ValueType, initialCapacity)
```

## 变量

声明变量的一般形式是使用 var 关键字：

```go
var identifier type
```

可以一次声明多个变量：

```go
var identifier1, identifier2 type
```

### 变量声明

#### 第一种，指定变量类型，如果没有初始化，则变量默认为零值。

```go
var v_name v_type
v_name = value
```

零值就是变量没有做初始化时系统默认设置的值。

```go
package main
import "fmt"
func main() {

    // 声明一个变量并初始化
    var a = "RUNOOB"
    fmt.Println(a)

    // 没有初始化就为零值
    var b int
    fmt.Println(b)

    // bool 零值为 false
    var c bool
    fmt.Println(c)
}
```

#### 第二种，根据值自行判定变量类型。

```go
var v_name = value
```

```go
package main
import "fmt"
func main() {
    var d = true
    fmt.Println(d)
}
```

#### 第三种，如果变量已经使用 var 声明过了，再使用 := 声明变量，就产生编译错误，格式：

简化声明赋值

```go
v_name := value
```

#### 多变量声明

```go
//类型相同多个变量, 非全局变量
var vname1, vname2, vname3 type
vname1, vname2, vname3 = v1, v2, v3

var vname1, vname2, vname3 = v1, v2, v3 // 和 python 很像,不需要显示声明类型，自动推断

vname1, vname2, vname3 := v1, v2, v3 // 出现在 := 左侧的变量不应该是已经被声明过的，否则会导致编译错误


// 这种因式分解关键字的写法一般用于声明全局变量
var (
    vname1 v_type1
    vname2 v_type2
)
```

#### 常量

常量的定义格式：

```go
const identifier [type] = value
```

你可以省略类型说明符 [type]，因为编译器可以根据变量的值来推断其类型。

- 显式类型定义： `const b string = "abc"`  

- 隐式类型定义： `const b = "abc"`

多个相同类型的声明可以简写为：

```go
const c_name1, c_name2 = value1, value2
```

## 函数

### 函数定义

Go 语言函数定义格式如下：

```go
func function_name( [parameter list] ) [return_types] {
   函数体
}
```

函数定义解析：

- func：函数由 func 开始声明
- function_name：函数名称，参数列表和返回值类型构成了函数签名。
- parameter list：参数列表，参数就像一个占位符，当函数被调用时，你可以将值传递给参数，这个值被称为实际参数。参数列表指定的是参数类型、顺序、及参数个数。参数是可选的，也就是说函数也可以不包含参数。
- return_types：返回类型，函数返回一列值。return_types 是该列值的数据类型。有些功能不需要返回值，这种情况下 return_types 不是必须的。
- 函数体：函数定义的代码集合。

以下实例为 max() 函数的代码，该函数传入两个整型参数 num1 和 num2，并返回这两个参数的最大值：

```go
/* 函数返回两个数的最大值 */  
func max(num1, num2 int) int {  
   /* 声明局部变量 */  
   var result int  

   if (num1 > num2) {  
      result = num1  
   } else {  
      result = num2  
   }  
   return result  
}
```

## 范围（Range）

Go 语言中 range 关键字用于 for 循环中迭代数组(array)、切片(slice)、通道(channel)或集合(map)的元素。在数组和切片中它返回元素的索引和索引对应的值，在集合中返回 key-value 对。

for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。格式如下：

```
for key, value := range oldMap {
    newMap[key] = value
}
```

## 错误处理

## 并发

## 面向对象

## 接口

# go例子

## 第一个go程序"`hello world`"

```go
package main

import "fmt"

func main() {
    fmt.Println("hello world")
}
```

要运行这个程序，将这些代码放到 `hello-world.go` 中并且使用 `go run` 命令。

```go
$ go run hello-world.go
hello world
```

有时候我们想将我们的程序编译成二进制文件。我们可以通过 `go build` 命来达到目的。

```go
$ go build hello-world.go
$ ls
hello-world    hello-world.go
```

然后我们可以直接运行这个二进制文件。

```go
$ ./hello-world
hello world
```

## 声明变量

```go
package main

import "fmt"

func main() {

  // var 声明 1 个或者多个变量。
    var a string = "initial"
    fmt.Println(a)

 // 你可以申明一次性声明多个变量。
    var b, c int = 1, 2
    fmt.Println(b, c)

// Go 将自动推断已经初始化的变量类型。

    var d = true
    fmt.Println(d)

// 声明变量且没有给出对应的初始值时，变量将会初始化为零值 。例如，一个 int 的零值是 0。

    var e int
    fmt.Println(e)

// := 语句是申明并初始化变量的简写，例如这个例子中的 var f string = "short"。


    f := "short"
    fmt.Println(f)
}
```

## for是 Go 中唯一的循环结构。

```go
package main

import "fmt"

func main() {

// 最常用的方式，带单个循环条件。
    i := 1
    for i <= 3 {
        fmt.Println(i)
        i = i + 1
    }

// 经典的初始化/条件/后续形式 for 循环。


    for j := 7; j <= 9; j++ {
        fmt.Println(j)
    }

// 不带条件的 for 循环将一直执行，直到在循环体内使用了 break 或者 return 来跳出循环。


    for {
        fmt.Println("loop")
        break
    }
}
```

## 函数

```go
package main
import "fmt"

// 这里是一个函数，接受两个 int 并且以 int 返回它们的和
func plus(a int, b int) int {
// Go 需要明确的返回值，例如，它不会自动返回最后一个表达式的值
    return a + b
}

func main() {
// 正如你期望的那样，通过 name(args) 来调用一个函数，
    res := plus(1, 2)
    fmt.Println("1+2 =", res)
}
```
