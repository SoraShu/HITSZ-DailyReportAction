# HITSZ-DailyReportAction

A fork of [HITSZ-DailyReport](https://github.com/CH3CHOHCH3/HITSZ-DailyReport) by [CH3CHOHCH3](https://github.com/CH3CHOHCH3)

一个基于 bash 和 github action 的开箱即用的自动上报脚本。基于原脚本调整了传参方式，增加了 github action 功能。

## :warning: 免责声明

:warning: 本脚本仅用作学习交流。

:warning: 本脚本所使用的上报信息来自用户自行获取的正确信息。由操作不当或恶意修改上报数据产生的一切后果本项目作者概不负责。

:warning: 本脚本仅适用于上报信息没有变化的情况，若需上报的信息发生变化请停止使用本脚本，正确上报信息。若上传了错误的信息产生的一切后果作者概不负责。

## quickstart

1. fork 本仓库。
2. 设置仓库 secrets。<sup>[how?](#设置-secrets)</sup>
3. 开启 github action 。<sup>[how?](#开启-github-action)</sup>

## 设置 secrets

为保护个人登录凭据和个人隐私，使用 secrets 保存账户信息和上报信息。

settings -> secrets -> actions -> New repository secrets

| Name     | Value                          |
| -------- | ------------------------------ |
| username | 学号                           |
| password | 统一认证密码，或者叫教务网密码 |
| info     | 按下面的步骤获取               |

### 获取 `info`

`info` 与上报内容有关。按照下方给出的方法获取。

由于每个人的上报内容各不相同，在此展示如何获得自己的上报内容。

首先打开疫情上报的页面，填好所需上报的内容。

随后按<kbd>F12</kbd>打开开发者工具，然后再点击提交。在开发工具的网络项中找到 save 项，并复制为 cURL(bash):

<div align="center"><img width=50% src="./explain.png"></div>

复制下来的内容中的`--data-raw`一项即为 `info`的值 。

一个例子：

```
info%3D%7B%22model%22%3A%7B%22dqzt%22%3A%2299%22%2C%22gpsjd%22%3A115.85517%2C%22gpswd%22%3A39.05549%2C%22kzl1%22%3A%221%22%2C%22kzl2%22%3A%22%22%2C%22kzl3%22%3A%22%22%2C%22kzl4%22%3A%22%22%2C%22kzl5%22%3A%22%22%2C%22kzl6%22%3A%22%E5%96%B5%E5%96%B5%E7%9C%81%22%2C%22kzl7%22%3A%22%E5%96%B5%E5%96%B5%E5%B8%82%22%2C%22kzl8%22%3A%22%E5%96%B5%E5%96%B5%E5%8C%BA%22%2C%22kzl9%22%3A%22%E5%96%B5%E5%96%B5%E8%B7%AF1%E5%8F%B7%22%2C%22kzl10%22%3A%22%E5%96%B5%E5%96%B5%E7%9C%81%E5%96%B5%E5%96%B5%E5%B8%82%E5%96%B5%E5%96%B5%E5%8C%BA%E5%96%B5%E5%96%B5%E8%B7%AF1%E5%8F%B7%22%2C%22kzl11%22%3A%22%22%2C%22kzl12%22%3A%22%22%2C%22kzl13%22%3A%220%22%2C%22kzl14%22%3A%22%22%2C%22kzl15%22%3A%220%22%2C%22kzl16%22%3A%22%22%2C%22kzl17%22%3A%221%22%2C%22kzl18%22%3A%220%3B%22%2C%22kzl19%22%3A%22%22%2C%22kzl20%22%3A%22%22%2C%22kzl21%22%3A%22%22%2C%22kzl22%22%3A%22%22%2C%22kzl23%22%3A%220%22%2C%22kzl24%22%3A%220%22%2C%22kzl25%22%3A%22%22%2C%22kzl26%22%3A%22%22%2C%22kzl27%22%3A%22%22%2C%22kzl28%22%3A%220%22%2C%22kzl29%22%3A%22%22%2C%22kzl30%22%3A%22%22%2C%22kzl31%22%3A%22%22%2C%22kzl32%22%3A%221%22%2C%22kzl33%22%3A%22%22%2C%22kzl34%22%3A%7B%7D%2C%22kzl38%22%3A%22%E5%96%B5%E5%96%B5%E7%9C%81%22%2C%22kzl39%22%3A%22%E5%96%B5%E5%96%B5%E5%B8%82%22%2C%22kzl40%22%3A%22%E5%96%B5%E5%96%B5%E5%8C%BA%22%7D%2C%22token%22%3A%22acbaddadadc%22%7D
```

> 实际上上述的 `--data-raw` 项为 encode 过后的上报信息。

## 开启 github action

若仓库上方没有一个明晃晃的 action ，那么去 settings ，侧栏找到 action ，然后选择 allow all action 。action 开启后会在每天 7:00 (23:00 UTC) 执行。需要停止脚本运行也是在这里 disable action 。

首次设置后可能希望手动运行一次 action ，可以在 上方的 action 中选择 action -> Auto Run Daily -> run workflow -> run workflow 。

action 可开启全局邮件提醒。右上角头像处 settings -> notifications -> actions -> 取消勾选 Send notifications for failed workflows only 。于是每次 action 运行结束就会发邮件通知。

## Note

如需要本地运行脚本，推荐使用原脚本 [HITSZ-DailyReport](https://github.com/CH3CHOHCH3/HITSZ-DailyReport) ，该脚本有更多可定制选项。

有技术问题欢迎提 issue 。
