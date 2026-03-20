# Python安装

## 这一页是干什么的
把 Python 环境装到“能稳定跑 GUI 与数据导出”状态，而不是只装解释器。

## 你会学到什么
- 推荐 Python 版本范围与原因
- 安装后必须做的可执行检查
- 与 GUI 依赖兼容性相关的关键点

## 先决条件
- [[06-软件环境搭建/02-Git与GitHub基础]]

## 预计耗时
- 20~40 分钟

## 正文
### 原理先讲清
`red-panda-afm/gui` 依赖 `PyQt6 + pyqtgraph + pyserial + numpy + tifffile`。版本太旧或混用系统 Python 常导致 Qt 启动失败或包冲突。

### 推荐版本
- 推荐：Python `3.10` 或 `3.11`
- 可尝试：`3.12`（若遇包兼容问题优先回退到 3.11）

### 一步一步怎么做
1. 安装 Python（勾选将 Python 加入 PATH）。
2. 验证解释器：
   ```bash
   python --version
   python -c "import sys; print(sys.executable)"
   ```
3. 验证 pip：
   ```bash
   python -m pip --version
   ```
4. 先升级打包工具：
   ```bash
   python -m pip install --upgrade pip setuptools wheel
   ```

### 每一步完成后怎么检查
- `python --version` 输出预期版本。
- `sys.executable` 指向你当前机器可控路径（不是奇怪临时路径）。
- `pip` 与该解释器绑定。

### 出错时先看哪里
- `python` 命令找不到：PATH 未配置。
- 版本不对：系统内有多个 Python，后续请固定使用虚拟环境。
- pip SSL 失败：检查网络/证书设置。

### 暂时做不到也没关系的部分
- 不急着全局安装任何 GUI 包，下一页会在 venv 内做。

## 用最简单的话再说一遍
先装对 Python，再装包；版本错了，后面都在补锅。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm.py`
- `red-panda-afm/gui/afm_gui.py`

## 这一页完成后，你应该能做到什么
- 用同一个解释器稳定执行 Python 命令
- 为虚拟环境创建做好准备

## 常见误区
- 直接用系统自带 Python 做项目环境
- 全局乱装包导致多个项目互相污染

## 下一页
- [[06-软件环境搭建/04-创建Python虚拟环境]]
- [[06-软件环境搭建/05-安装PyQt6等依赖]]

## 导航
- 上一页：[[06-软件环境搭建/02-Git与GitHub基础]]
- 下一页：[[06-软件环境搭建/04-创建Python虚拟环境]]
- 返回首页：[[00-首页/00-首页]]
