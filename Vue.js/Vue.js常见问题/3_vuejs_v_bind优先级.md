## [ v-bind: / : ] 绑定值的优先级

1. 先在行内找变量
2. 然后在vue data中找变量
3. 找不到就报错

```
<div>
    <ul>
    	<li v-for="item in items" :value="item">{{item}}</li> //------------------ 1. v-bind: 优先行内找变量
    </ul>
</div>

...

data() {
return {
        msg: "helloworld",
        item: "haha", //------------------ 2. 然后vue data中找变量
        items: [232342, 34, 234, 234, 23, 42, 34, 234, 234, 4, 5, 5, 76],
    };
},
```

