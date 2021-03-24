```
# vuejs v-for

# Array
v-for="item in items" // Array ???js中不是这样???
v-for="(item, index) in items" // 【类似于reactjs遍历array：使用array.map((item, index)=>{})】

v-for="item of items" // Array
v-for="(item, index) of items"

# Object
v-for="value in object" // Object
v-for="(value, key) in object"
v-for="(value, key, index) in object" 

v-for="value of object" // Object XXXjsXXX
v-for="(value, key) of object"
v-for="(value, key, index) of object" 
```

