

# Python自动备份、编译、上传项目脚本

[toc]

## 思路

- 通过sftp备份服务器部署项目【放到本地备份目录（根据时间建文件夹）】
- python调用cmd执行mvn打包命令【复制idea控制台mvn命令】【切换开发 / 生产环境配置】【重命名包】
- 通过sftp上传到服务器部署项目的目录

## 具体

### pysftp【连接sftp】

> https://pypi.org/project/pysftp/

```python
import pysftp

with pysftp.Connection('hostname', username='root', password='root') as sftp:
	with sftp.cd('/home/projects'): # 服务器部署项目位置
		sftp.get('demo.war') # 下载本地服务器项目（此时已经在cd的目录下面了）
		sftp.put(r'D:\Projects\demo.war') # 上传本地项目
```

- python3.9测试pysftp没问题【注意版本匹配问题】
- 如果aliyun mirror中下载卡住就[手动下载](https://pypi.python.org/pypi/pysftp)，然后`$ python3 setup.py install`即可

### time / os / shutil【生成时间文件夹 / 移动文件】

```python
import time
import os
import shutil

def currentDatetime():
	# %Y-%m-%d %H:%M:%S
	return str(time.strftime("%Y-%m-%d_%H%M%S", time.localtime()))

# os.listdir(x)
# os.makedirs(x)
# os.path.exists(x)
# os.path.join(x, y)
# os.path.abspath(x)
# os.rename(x, y)
# ...

shutil.move(srcpath, despath)
```

### subprocess / os【pytyhon执行cmd命令】

```python
import subprocess

# cmd中可以用&来组合命令
# cmd中先选磁盘【D:】，再【cd xxx】
# 如果cmd命令中有", 字符串外面就用''包围
# ... 可以在idea中点击按钮执行maven clean / package【输出的首行会有mvn执行命令，复制过来就行】【执行cmd需要cd到项目目录下面，因为复制的mvn命令是在项目目录下面执行的】

cmd_mvn_clean = r"D: & cd D:\Projects\ & ..."
cmd_mvn_package = r"...."

# wait()会等待cmd命令执行结束再下一步操作【用os.system()就不会等待】【推荐subprocess】
status_code_clean = subprocess.Popen(cmd_mvn_clean, shell=True).wait()
status_code_package = subprocess.Popen(cmd_mvn_package, shell=True).wait()

# tips:
# 在打包之前可以`active: production`
# 打包ing...
# 打包之后可以`active: development`
def active_production_development(condition):
    	... # 文件IO修改active:行就好了【打包好了之后，在换回来本地开发配置】
```

## 备注

- 自动备份、编译、上传【固定模式】，所以异常情况没有考虑【仅记录思路】
- 可以搞个小系统【管理多个项目走一套流程（备份 | 编译 | 上传 | ...），列表展示详情信息、操作、记录操作IP、线上项目状态等】
- 应该有开源的项目部署管理系统，或者部署流程工具【可以分享一下】