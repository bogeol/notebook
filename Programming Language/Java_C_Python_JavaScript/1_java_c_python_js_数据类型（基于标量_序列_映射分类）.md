# 1_java_c_python_js_数据类型（基于标量、序列、映射分类）

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

### 操作【CRUD】

- [x] 添加【C】
- [x] 获取【R】
- [x] 更新【U】
- [ ] 删除【D】
- [ ] 其他
  - [ ] 清空
  - [ ] 过滤
  - [ ] 去重
  - [ ] 统计
  - [ ] 。。。

```java
        /**
         * 1. Array [ fixed size / fixed data type ] [CRUD]
         * - array[index] = element
         * - array[index]
         * - array[index] = element
         * - TODO
         */
        Object[] objects = new Object[3];
        objects[0] = "xx";
        objects[1] = 12;
        System.out.println(Arrays.asList(objects));

        Object[] objects_ = new Object[]{1, 2, 3};
        System.out.println(Arrays.asList(objects_));

        Object[] objects__ = {true, "haha", 3};
        System.out.println(Arrays.asList(objects__));

        /**
         * 2. List [dynamic array] [CRUD]
         * - add(element)
         * - get(index)
         * - set(index, element)
         * - remove(index)
         */
        List list = new ArrayList();
        list.add("xx");
        list.add(true);
        list.add(123);
        System.out.println(list.get(0)); // List -> {0: element0, 1: element1, ...} 【类似于key为默认自增数字的Map】
        System.out.println(list.get(1));
        System.out.println(list.get(2));
        list.set(2, "new item");
        list.remove(0);
        System.out.println(list);

        /**
         * 3. Set
         * - add(element)
         */
        Set set = new HashSet();
        set.add("xx");
        set.add(123);
        set.add(true);
        System.out.println(set);

        /**
         * 4. Map [CRUD]
         * - put(key, value) # C
         * - get(key) # R
         * - put(key, value) # U
         * - remove(key) # D
         */
        Map map = new HashMap();
        map.put("name", "xiaoming");
        map.put("age", 20);
        map.put("status", false);
        map.put("temp", null);
        System.out.println(map.get("name"));
        System.out.println(map.get("age"));
        System.out.println(map.get("status"));
        map.put("status", true);
        map.remove("temp");
        System.out.println(map);
```

### 遍历

- [遍历list](https://www.baeldung.com/java-iterate-list)
- [遍历map](https://stackoverflow.com/questions/46898/how-do-i-efficiently-iterate-over-each-entry-in-a-java-map)

```java
        /**
         * Array
         */

        /**
         * - for index
         * - for in [:]
         */
        Object[] objects = {1, 2, 3, 23, 2, 32, 3, 2};
        for (int i = 0; i < objects.length; i++) {
            System.out.println(objects[i]);
        }
        for (Object object : objects) {
            System.out.println(object);
        }

        /**
         * List / Set / Queue / ...【差不多】
         */

        /**
         * loop
         * - for
         *     - for index
         *     - for in [:]
         * - forEach
         *     - Iterable forEach
         *     - Stream forEach
         * - Iterator
         *     - Iterator
         *     - ListIterator
         */

        List list = new ArrayList();
        list.add(1);
        list.add(2);
        list.add(3);

        // for index
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }

        // for in【:】
        for (Object object : list) {
            System.out.println(object);
        }

        // Iterable forEach
        list.forEach(e -> System.out.println(e));

        // Stream forEach
        list.stream().forEach(e -> System.out.println(e));

        // Iterator
        Iterator iterator = list.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }

        // ListIterator
        ListIterator listIterator = list.listIterator();
        while (listIterator.hasNext()) {
            System.out.println(listIterator.next());
        }


        /**
         * Map
         */

        /**
         * loop
         * - for in entry
         * - for in key
         * - iterable forEach
         * - iterator entry
         * - entry > stream
         * - entry > stream parallel
         */

        Map<String, Object> map = new HashMap();
        map.put("name", "xiaowang");
        map.put("age", 20);
        map.put("status", false);

        // for in entry
        for (Map.Entry<String, Object> entry : map.entrySet()) {
            System.out.println(entry);
        }

        // for in key
        for (String key : map.keySet()) {
            System.out.println(map.get(key));
        }

        // Iterable forEach
        map.forEach((k, v) -> System.out.println(k + v));

        // iterator entry
        Iterator<Map.Entry<String, Object>> mapIterator = map.entrySet().iterator();
        while (mapIterator.hasNext()) {
            System.out.println(mapIterator.next());
        }

        // entry => stream
        map.entrySet().stream().forEach(e -> System.out.println(e));

        // entry => stream parallel
        map.entrySet().stream().parallel().forEach(e -> System.out.println(e));

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

- python官网
- [python list删除元素](https://note.nkmk.me/en/python-list-clear-pop-remove-del/)

```python
    # list [CRUD]-----------------------------------
    # - x.append # C
    # - x[index] # R
    # - x[index] = element # U
    # - D
    #   - x.pop(index)
    #   - x.remove(element)
    #   - del x[index]

    list_ = []
    list_.append(1)
    list_.append(True)
    list_.append("xxx")
    list_.append(list(range(5)))
    list_.append(random.random())

    print(list_[0])
    print(list_[1])

    print(list_)
    list_.pop(0)  # by index
    list_.remove("xxx")  # by element
    del list_[-1]
    print(list_)

    # set-----------------------------------
    # - x.add(element)
    # - x.remove(element)
    set_ = set()
    set_.add("xx")
    set_.add(1)
    set_.add(range(10))

    print(set_)
    set_.remove(1)
    print(set_)

    # tuple-----------------------------------
    # - x = () # first init [immutable]
    # - x[index]
    # - x[index]... # inner mutable element can be changed
    tuple_ = (1, 2, 3, [4, 5])
    print(
        tuple_)  # TypeError: 'tuple' object does not support item assignment => However, innet item of mutable element can be changed
    print(tuple_[0])
    print(tuple_[1])

    tuple_[-1].append("inner mutable list")
    print(tuple_)

    # dict[CRUD]-----------------------------------
    # - x[key]=value / {} init
    # - x[key] / x.get(key)
    # - x[key] = element
    # - del x[key]
    dict_ = {
        "name": "xiaowang",
        "age": 20,
        "status": False
    }
    print(dict_)
    dict_["temp"] = None  # Create
    print(dict_)

    print(dict_.get("temp"))  # Retrive
    print(dict_["temp"])

    dict_["status"] = True  # Update
    del dict_["temp"]  # Delete
    print(dict_)
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