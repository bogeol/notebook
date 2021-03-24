# js loop

- Array（自带索引的Object）
- Object（kv对象）

```javascript
# 常用方法：
1. for index
2. for key in object [Object]
3. for item of array [Object:Array]

#######################js VS py
list_ = [23,2,2,3,33524,2,34,234,2354,23]cC
for item in list_: # py loop list
    print(item)
dict_ = {
        "name": "xiaowang",
        "age": 20,
        "status": False,
    }
for key in dict_: # py loop dict | **js loop Object [Array / Object / ...]**
    print(key)
#######################

#######################js
      var x = [1, 2, 2, 2, 2, 2, 3, 42, 34, 23, 4];
      var y = {
        data: [23, 23, 23, 23, 23, 23, 4544554, 4, 4, 34],
        msg: "test",
      };
      // js loop Object [Array / Object / ...]
      for (let key in x) {
        console.log(key, x[key]); // key ~~~ index
      }
      for (let key in y) {
        console.log(key, y[key]);
      }
      // js loop Object:Array [ES6]
      for (let item of x) {
        console.log(item);
      }
#######################
 
# 其他方法
// 正序参数
4. Object.entries(object).forEach(([k, v]) => {})
5. Object.entries(object).map(([k, v]) => {})

// 逆序参数【Object:Array】
6. array.forEach((item, index, array) => {}) [Array.prototype.forEach]
7. array.map((item, index, array) => {})

#######################js
// Object.entries(object) > forEach / map > 正序参数
Object.entries(object).forEach(([key, value]) => {
  console.log(key, value);
});
Object.entries(object).map(([key, value]) => {
  console.log(key, value);
});

// array > forEach / map > 逆序参数【Object:Array】
array.forEach((item, index, array) => {
        console.log(item, index, array);
      });
array.map((item, index, array) => {
        console.log(item, index, array);
      });
#######################

# PS
object.keys()
object.values()
object.entries()
```

