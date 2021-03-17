# mdn html

- **HTML(HyperText Markup Language)**
  - 告知浏览器如何组织页面的**标记语言【**由一系列的**元素（[elements](https://developer.mozilla.org/en-US/docs/Glossary/Element)）**组成**】**

- **定义文档**
  - 声明文档类型
  - 新建文档标签
    - 新建头部标签
    - 新建主体标签

```
<!DOCTYPE html> # 1. 声明文档类型
<html> # 2. 新建文档标签
  <head> # 2.1 新建头部标签【metadata】
  </head>
  <body> # 2.2 新建主体标签【content】
  </body>
</html>
```

- **定义元素**
  - 元素标签
  - 元素内容
  - 元素属性【k="v"属性 / 布尔属性】

```
- <p></p> # 标签
- <p>content: ...</p> # 内容
- <p class="content">content: ...</p> # k="v"属性
- <input type="text" disabled></input> # 布尔属性
```

- HTML标签不区分大小写【一般是用小写】

  ![image](1_mdn_html.assets/1615193698666-0d6c6de4-c2db-43b3-89b8-a1e8f173a7a7.png)
- 所有的元素都需要正确的打开和关闭，这样才能按你所想的方式展现
- 把元素放到其它元素之中——这被称作嵌套
- **元素类别**
  - 块级元素【block】
  - 内联元素【inline】【通常是块中环绕文本内容的部分】
  - 空元素【empty element】【eg： `<img src="" />` 】
- 元素属性
- HTML中特殊字符

```
原义字符	等价字符引用
<	&lt;
>	&gt;
"	&quot;
'	&apos;
&	&amp;
    &nbsp;
```

## 参考

- https://html.spec.whatwg.org/multipage/
- [https://developer.mozilla.org/zh-CN/docs/learn/HTML/](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Getting_started)