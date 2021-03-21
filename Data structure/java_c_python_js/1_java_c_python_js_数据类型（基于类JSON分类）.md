# 1_java_c_python_js_数据类型（基于类JSON分类）

## 前言

- **Scalar【标量】**
  - Number
  - String
  - Boolean
  - ...
- **Sequence【序列】**
  - List
  - Set
  - ...
- **Mapping【映射】**
  - Map
  - ...

## java

- **Scalar**
  - Number
    - byte【1byte(s)】
    - short【2byte(s)】
    - int【4byte(s)】
    - long【8byte(s)】
    - float【4byte(s)】
    - double【8byte(s)】
  - String
    - char【2byte(s)】【注意：java.lang.String为Object】
  - Boolean
    - boolean
- **Sequence**
  - Array
  - List
  - Set
  - Queue
  - ...
- **Mapping**
  - Map
  - ...

### 新建

```java
        // 1. Primitive Types【原始类型】
        /**
         * java:【各进制前缀表示】
         * - 二进制【0B】
         * - 八进制【0】
         * - 十进制【】
         * - 十六进制【0X】
         */
        byte byte_ = 0B00000001;
        short short_ = 1;
        int int_ = 1;
        long long_ = 1L; // 后缀：l / L都可以【推荐大写】【下面同样的】
        float float_ = 1.0F;
        double double_ = 1.0D;
        char char_ = 'a';
        boolean boolean_ = true;

        // 2. Non-Primitive Types / Reference Types【非原始类型 / 引用类型】
        Object[] objects = new Object[10];
        List list_ = new ArrayList();
        Set set_ = new HashSet();
        Queue queue_ = new PriorityQueue();
        Map map = new HashMap();
```

### 操作

```

```

### 遍历

```

```



## c



## python

- **Scalar**
  - Number
    - int
    - float
    - complex
  - String
    - str【注意：python官网将str归为Text Sequence Type】
  - Boolean
    - bool
- **Sequence**
  - list
  - set【注意：A set object is an unordered collection of distinct hashable objects.】
  - tuple
  - range【注意：The range type represents **an immutable sequence of numbers** and is commonly used for **looping a specific number of times** in for loops.】
- **Mapping**
  - dict

### 新建

```python
# 1. Primitive Types
a = 1
b = 1.0
c = complex(2, -3)

# 2. Non-Primitive Types
list_ = []
set_ = set() # {}被dict占用了，所以**定义set类型必须要用set()**【实际上list() set() tuple() dict()都可以用来定义】
tuple_ = ()
range_ = range(10) # range(n) => [0, n) ||| range(x, y) => [x, y) 
dict_ = {}

# ps:
print(x)
print(type(x))
print(len(x))
...
```

### 操作

```

```

### 遍历

```

```



## js

- **Scalar**
  - Number
  - String
  - Boolean
  - Null
  - Undefined
  - Bigint
  - Symbol
- **Sequence**
  - Array
- **Mapping**
  - Object

### 新建

```javascript
      // 1. Primitive Types
      var number_ = 1;
      var string_ = "test";
      var boolean_ = false;
      var null_ = null; // refer null 【PS：typeof null ~ Object】
      var undefined_; // not assigned
      var bigint_ = 1n;
      var symbol_ = Symbol("x"); // data type whose instances are unique and immutable

      // 2. Non-Primitive Types【js中非原始类型全部属于对象】
      /**
       * JavaScript Object
       *    - Function # () => {} / function () {}
       *    - new Array() # []
       *    - new Object() # {}
       *    - new Set()
       *    - new Map()
       *    - new WeakMap()
       *    - new WeakSet()
       *    - new Date()
       */
      var function_ = () => {};
      var array_ = new Array();
      var object_ = new Object();
      var set_ = new Set();
      var map_ = new Map();
      var date_ = new Date();
      //...

      // PS
      console.log(x);
      console.log(typeof x);
      console.log(x.length);
```

### 操作

```

```

### 遍历

```

```



## 参考

- [阮一峰：数据类型和JSON格式](http://www.ruanyifeng.com/blog/2009/05/data_types_and_json.html)
- 