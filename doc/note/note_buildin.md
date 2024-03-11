# buildin 部分源码笔记

1. 基本类型
    - 整数类型
      - 无符号:
        * byte / uint8 [0, 255]
        * uint16 [0, 65535]
        * uint / uint32 [0, 4294967295]
        * uint64 [0, 18446744073709551615]
      - 有符号:
        * int8 [-128, 127]
        * int16 [-32768, 32767]
        * int / rune(字符) / int32 [-2147483648, 2147483647]
        * int64 [-9223372036854775808, 9223372036854775807]
    - 浮点类型
        * float32
        * float64
    - 复数类型
        * complex64 [2 * float32 表示实数部分和虚数部分]
        * complex128 [2 * float64 表示实数部分和虚数部分]
    - 字符串类型
        * string 
    - 指针类型
        * uintptr
    - 接口类型
        * interface 
            - 空接口 any = interface{}
            - 非空接口
    - 空类型
      * nil

2. 内建函数
    append: 向切片末端添加元素
    ```go
        func append(slice []Type, elems ...Type) []Type
    ```
    特殊情况: 可以将字符串添加到字节切片当中。
    ```go
        slice = append([]byte("hello "), "world"...)
    ```
   
    copy: 切片拷贝 / 字符串拷贝到切片中 
    ```go
        func copy(dst, src []Type) int
    ```
   
    delete: 从map中删除指定key元素 (nil/不存在则不处理)
    ```go
        func delete(m map[Type]Type1, key Type)
    ```

    len: 根据参数类型获取参数的长度
        Array: 获取元素个数
        *Array: 获取元素个数 (包括 nil)
        slice/map: 获取值的个数 (不包括值为 nil)
        string: 获取字节数
        channel: 获取管道缓冲区中未读元素个数 (不包括 nil)
    ```go
        func len(v Type) int
    ```
   
    cap: 获取参数的容量
        Array: 获取数组长度
        *Array: 获取数组长度
        slice: 获取切片最大可容纳长度
        channel: 获取管道缓冲区容量 (最大可容纳元素个数)
    ```go
        func cap(v Type) int
    ```
   
    make: 分配并初始化对象
        作用: 
            1. 根据类型分配对应类型的内存空间
            2. 完成对象的初始化

        Slice: 
        Map:
        Channel:
    ```go
        func make(t Type, size ...IntegerType) Type  
    ```

    new: 分配对象内存空间并获取对象指针
    ```go
        func new(Type) *Type
    ```

    * make 与 new 区别:

    