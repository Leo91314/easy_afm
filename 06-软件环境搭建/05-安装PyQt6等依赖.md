# 安装PyQt6等依赖

## 这一页是干什么的
把 GUI 的运行依赖一次装齐并做导入验证，确保后续能直接启动 `afm_gui.py`。

## 你会学到什么
- 从源码反推依赖清单的方法
- GUI 最小依赖安装命令
- 常见安装失败场景与排查路径

## 先决条件
- [[06-软件环境搭建/04-创建Python虚拟环境]]

## 预计耗时
- 25~50 分钟

## 正文
### 原理先讲清
`red-panda-afm/gui/afm.py` 和 `afm_gui.py` 的 import 就是你的真实依赖来源。当前仓库未提供现成 `requirements.txt`，所以需要手工装核心包。

### 从源码提取出的核心依赖
- `PyQt6`
- `pyqtgraph`
- `pyserial`
- `numpy`
- `tifffile`

### 一步一步怎么做
1. 激活虚拟环境后安装依赖：
   ```bash
   cd red-panda-afm/gui
   source .venv/bin/activate  # Windows 改用对应激活命令
   pip install PyQt6 pyqtgraph pyserial numpy tifffile
   ```
2. 做批量导入测试：
   ```bash
   python -c "import PyQt6,pyqtgraph,serial,numpy,tifffile; print('GUI deps OK')"
   ```
3. 生成本地依赖锁定文件：
   ```bash
   pip freeze > requirements-local.txt
   ```

### 每一步完成后怎么检查
- 导入测试输出 `GUI deps OK`。
- `requirements-local.txt` 包含以上核心依赖。
- 没有出现 `ModuleNotFoundError`。

### 出错时先看哪里
- Qt 安装失败：确认 Python 版本是否过新，必要时降到 3.11。
- 网络下载慢/失败：使用稳定镜像源重试。
- 安装成功但导入失败：大概率不是当前 venv。

### 暂时做不到也没关系的部分
- 串口设备驱动暂时可不装，先完成 GUI 启动链路。

## 用最简单的话再说一遍
先让 import 全绿，再谈界面和硬件。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm.py`
- `red-panda-afm/gui/afm_gui.py`

## 这一页完成后，你应该能做到什么
- 在一条命令里验证 GUI 依赖是否完整
- 对后续 GUI 报错定位更快（先分依赖问题还是业务问题）

## 常见误区
- 看到 `pip install` 成功就以为可运行，实际上没做导入验证
- 把 UI 文件问题误判为依赖问题

## 下一页
- [[06-软件环境搭建/06-安装PlatformIO]]
- [[06-软件环境搭建/09-如何打开gui项目]]

## 导航
- 上一页：[[06-软件环境搭建/04-创建Python虚拟环境]]
- 下一页：[[06-软件环境搭建/06-安装PlatformIO]]
- 返回首页：[[00-首页/00-首页]]
