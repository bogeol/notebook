# Chrome插件 - Surfingkeys - 用键盘更方便的操作浏览器

## 前言

官方介绍：Rich shortcuts to click links/switch tabs/scroll pages or capture full page, use your browser like vim for productivity.A Chrome extension for Vim users, but EMACS users would also love it, as it is much extendable with javascript.

简而言之：就是用键盘更方便的操作浏览器，以及自定义扩展功能。

## 一、安装配置

- Chrome Web Store中安装Surfingkeys插件 -> 左键点击插件 -> Settings -> Key mappings -> Advanced mode
- Loading settings from [Settings.txt](https://raw.githubusercontent.com/bogeol/settings-surfingkeys/master/settings/settings-surfingkeys.txt) -> 把链接复制进去即可 -> Save

## 二、常用按键

### 1.Page

| 按键 |     功能      |   备注   |
| :--: | :-----------: | :------: |
|  h   |     left      |    ←     |
|  j   |     down      |    ↓     |
|  k   |      up       |    ↑     |
|  l   |     right     |    →     |
|  c   |   scroll up   | [PG UP]  |
|  a   |  scroll down  | [PG DN]  |
|  gg  | scroll to top |  [HOME]  |
|  G   | scroll to end |  [END]   |
|  r   |  **r**efresh  | [Ctrl+R] |

### 2.Tab

| 按键 |     功能     |        备注        |
| :--: | :----------: | :----------------: |
|  e   | previous tab | [Ctrl+Shift+Tab] ↑ |
|  d   |   next tab   |    [Ctrl+Tab] ↓    |
|  x   |  close tab   |      [Ctrl+W]      |
|  X   |  reopen tab  |   [Ctrl+Shift+T]   |

### 3.History

| 按键 |       功能       | 备注 |
| :--: | :--------------: | :--: |
|  q   | previous history |  ←   |
|  w   |   next history   |  →   |

### 4.Search

| 按键  |               功能                |                       备注                        |
| :---: | :-------------------------------: | :-----------------------------------------------: |
| sg/og | search **g**oogle/open **g**oogle | s是搜索已复制或者选中的文字/o是打开搜索栏自行输入 |
| sb/ob |             **b**aidu             |                       同上                        |
| sd/od |          **d**uckduckgo           |                       同上                        |
| sh/oh |            git**h**ub             |                       同上                        |
| ss/os |         **s**tackoverflow         |                       同上                        |
| st/ot |       google **t**ranslate        |              同上（可修改搜索参数）               |
| sy/oy |            **y**outube            |                       同上                        |

### 5.Mouse

| 按键 |                 功能                  |        备注        |
| :--: | :-----------------------------------: | :----------------: |
|  f   | 根据hint选择鼠标点击 (空格键隐藏hint) |    select click    |
|  i   |          根据hint选择输入框           |    select input    |
|  gi  |           选择第一个输入框            | select first input |

## 三、其他按键

### 1.标签页

- `g0` 跳转到第一个标签页
- `g$` 跳转到最后一个标签页
- `gx0` 关闭当前标签左侧所有标签
- `gx$` 关闭当前标签右侧所有标签
- `gxx` 关闭当前标签之外所有标签
- `<<` 左移当前标签
- `>>` 右移当前标签
- `gt` 选择所有已打开的标签页
- `m[X]` 添加当前URL到标记字符X「eg : 标记当前页面`ma` , 然后在其他页面`'a`就跳转到这个标记页面了」
- `'[X]` 跳转到标记字符X的URL

### 2.打开浏览器内置功能

- `ga` About
- `gb` Bookmark
- `gc` Cache
- `gd` Download
- `gh` History
- `gk` Cookie
- `ge` Extension
- `gn` Net-Internal
- `gs` Source

### 3.会话

- `ZZ` 保存会话并退出
- `ZR` 恢复最近一次会话

### 4.剪切板

- `yy` 复制当前网页链接
- `yi` 复制输入框中的内容

### 5.BAR

- `t` 打开新网页bar
- `b` 打开收藏夹bar
- ~~`ab` 添加到收藏夹~~
- `<Shift-Tab>` 在Bar中切到上一个条目 ↑
- `<Tab>` 在Bar中切到下一个条目 ↓
- `<Ctrl-,>` 在Bar中显示上一页搜索结果
- `<Ctrl-.>` 在Bar中显示下一页搜索结果

### 6.其他功能按键

- `?` 打开帮助
- `etc.`

## 四、总结

- 可以键盘鼠标配合操作浏览器，常用就是`qw | ed | ca | t | x | o[g]/s[g]`
- 可以自定义配置（自定义快捷键，自定义快捷键的功能，主题等等）

