# java python 对象区别理解

## 定义对象区别

java:

```java
public class User {

    // class/static variables
    static String code = "sjdfkjskdf@sjdkx";

    // object/this variables[**default**][**this.**]
    String username;
    String password;
    boolean status;

    // constructor
    public User(String username, String password, boolean status) {
        this.username = username;
        this.password = password;
        this.status = status;
    }
}
```
python:

```python
class User:

    # class/static variables[**default**]
    code = "SXSj2s9SSFX" # [ class variable | self/object variable ]
	
    # constructor
    def __init__(self, username, password, status):
        # obejct/self variables
        self.username = username
        self.password = password
        self.status = status
```

- 定义对象出发点：【`默认约束 / 限定符 / 注解`】
  - **类**
    - **变量**
    - **方法**
  - **对象**
    - **变量**
    - **方法**
- java中【理念：变量/方法全都放在class中（默认变量/方法全部属于对象）（全部通过限定符来控制范围）】【★结构清晰★】
  - 定义在class中的变量默认就是对象变量【通过限定符来控制类/对象变量】【所有对象变量在class中定义，然后通过this指向】
  - 定义在class中的方法默认就是对象方法【通过限定符来控制类/对象方法】
- python中【理念：类变量放在class中 ||| 类方法通过注解控制范围 ||| 对象变量放在self中 ||| 对象方法放在class中】
  - 定义在class中的变量默认就是类变量【通过区块划分来控制类/对象变量】【所有对象变量都通过self来定义和指向】【ps：self只是习惯用法（实际上只要是第一个参数就是关键词），但是java中的this是关键词】

## 思路

- java中通过**限定符**来限制范围
  - 所有东西扔到class中，然后通过限定符来控制
- python由于没有限定符【所以要通过**约定+注解**来控制】
  - 假设以java class为参考（先全扔class里面）：
    - 默认类变量放在class中
    - 将对象变量扔到self中
    - 类方法通过注解控制
    - 默认对象方法放在class中

