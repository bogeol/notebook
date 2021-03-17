## 1_vuejs回车事件【事件处理】【按键修饰符】

```
vuejs操作：
@keyup.enter

原生js操作：
@onchange="show(event)"

js:
function show(event){
	console.log(event.keyCode);
}
```

> 实际上就是vue的特殊指令

## vuejs - 基础 - 事件处理 - 按键修饰符

> https://cn.vuejs.org/v2/guide/events.html

在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 `v-on` 在监听键盘事件时**添加按键修饰符：**

```
<input v-on:keyup.enter="submit">
<input v-on:keyup.page-down="onPageDown">
...
```

为了在必要的情况下支持旧浏览器，Vue 提供了绝大多数常用的按键码的别名：

- `.enter`
- `.tab`
- `.delete` (捕获“删除”和“退格”键)
- `.esc`
- `.space`
- `.up`
- `.down`
- `.left`
- `.right`

可以用如下修饰符来实现仅在按下相应按键时才触发鼠标或键盘事件的监听器。

- `.ctrl`
- `.alt`
- `.shift`
- `.meta`