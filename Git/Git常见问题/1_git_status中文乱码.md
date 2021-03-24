## git status的时候中文显示不出来，显示一段数字

> git-bash的编码已经设置了**zh_CN UTF-8**了，还是有问题

**问题：**

```
 $ git status
 ...
 new file:   "Vue.js/Vue.js\345\270\270\350\247\201\351\227\256\351\242\230/
 ...
```

**解决：**

```
$ git config --global core.quotepath false
```

