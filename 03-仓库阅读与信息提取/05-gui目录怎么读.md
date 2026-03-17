# gui目录怎么读

## 这一页是干什么的
帮助你把 GUI 目录拆成“入口文件 + 协议层 + 界面层”。

## 你会学到什么
- `afm.py` 和 `afm_gui.py` 各自角色
- GUI 依赖包从哪里看
- 如何判断 GUI 已经“基本可运行”

## 先决条件
- [[03-仓库阅读与信息提取/04-firmware目录怎么读]]
- [[06-软件环境搭建/05-安装PyQt6等依赖]]

## 预计耗时
- 30 分钟

## 正文
已确认：
- `afm.py`：设备通信与业务逻辑（串口、命令、扫描数据、导出 TIFF）
- `afm_gui.py`：PyQt6 界面（主窗口、Focus、Approach、Scan）
- 依赖可从 import 推断：`PyQt6`、`pyqtgraph`、`pyserial`、`numpy`、`tifffile`

建议先做：
1. 创建虚拟环境
2. 安装最小依赖
3. 直接运行 GUI，先看能否启动界面

## 用最简单的话再说一遍
`afm.py` 负责“跟设备说话”，`afm_gui.py` 负责“你看到的按钮和图”。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm.py`
- `red-panda-afm/gui/afm_gui.py`
- `red-panda-afm/gui/ui/*.ui`

## 这一页完成后，你应该能做到什么
- 分辨 GUI 的“通信层”和“界面层”
- 能列出最小依赖安装清单

## 常见误区
- 只装 PyQt6，漏装 pyserial/tifffile
- GUI 打开了就以为整机流程没问题

## 下一页
- [[12-GUI与上位机部分/01-gui项目总览]]
- [[06-软件环境搭建/09-如何打开gui项目]]
- [[03-仓库阅读与信息提取/06-pcb目录怎么读]]

## 导航
- 上一页：[[03-仓库阅读与信息提取/04-firmware目录怎么读]]
- 下一页：[[03-仓库阅读与信息提取/06-pcb目录怎么读]]
- 返回首页：[[00-首页/00-首页]]
