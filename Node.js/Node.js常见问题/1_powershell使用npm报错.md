## npm.ps1 cannot be loaded because running scripts is disabled on this system

报错：cmd运行npm没问题，但是powershell有问题

```
# 打开powershell
$ Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted

$ npm --version
```

## 参考：

- https://stackoverflow.com/questions/41117421/ps1-cannot-be-loaded-because-running-scripts-is-disabled-on-this-system