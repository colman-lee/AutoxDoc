# 从外部运行 Autox 脚本

Autox 提供了一些接口，支持从其他设备或 app 调用并运行脚本

## VsCode 插件

支持连接设备并进行开发调试等，由先前开发者编写，目前已许久没有维护，但目前任然兼容，  
[下载地址](https://marketplace.visualstudio.com/items?itemName=aaroncheng.auto-js-vsce-fixed)  
也可以在 VsCode 插件商店搜索`Autox.js`下载安装

## Autox cli 工具

> 需要 Autox V7 7.1.5 版本及以上，并且在侧边栏打开 usb 调试

支持通过 cli 运行项目及文件，保存项目到手机等，需要 nodejs 环境

- 安装

```
npm i autox-cli -g
```

- 运行脚本或项目

```
autox run path
```

将 path 替换为要运行的脚本文件或项目目录

- 保存项目到设备

```sh
autox save path
# or
autox save path --devip 192.168.1.111 --name 保存名称
```

path 必须是一个目录，会将该目录覆盖到脚本主目录文件夹

运行`autox -h`可查看所有命令

## 通过应用广播运行

- 显式调用

此方式会显示一个对话框提醒用户

```
adb shell am start -n org.autojs.autoxjs.v7/org.autojs.autojs.external.open.OpenIntentActivity -d "file:///sdcard/script.js"
```

- 隐式调用

> 此功能需要在设置中打开 "允许广播运行脚本" 开关

```
adb shell am start -n org.autojs.autoxjs.v7/org.autojs.autojs.external.open.RunIntentActivity -d "file:///sdcard/script.js"
```

app 应用中参考以上方式设置 intent 即可
