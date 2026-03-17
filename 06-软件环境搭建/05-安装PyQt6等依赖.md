# 安装PyQt6等依赖

## 这一页是干什么的
根据源码 import 反向提取最小依赖并安装。

## 你会学到什么
- 当前可推断依赖包
- 依赖安装命令
- 安装后验证方法

## 先决条件
- [[06-软件环境搭建/04-创建Python虚拟环境]]

## 预计耗时
- 20~30 分钟

## 正文
从 `gui/afm.py` 与 `gui/afm_gui.py` 的 import 可推断最小依赖：
- `PyQt6`
- `pyqtgraph`
- `pyserial`
- `numpy`
- `tifffile`

安装命令（在已激活 `.venv` 后执行）：
```bash
pip install PyQt6 pyqtgraph pyserial numpy tifffile
```

验证：
```bash
python -c "import PyQt6, pyqtgraph, serial, numpy, tifffile; print('ok')"
```

> [!note] 说明
> 仓库当前未看到 `requirements.txt`，以上依赖来自源码导入分析。

## 用最简单的话再说一遍
源码里 `import` 了什么，你就先装什么。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm.py`
- `red-panda-afm/gui/afm_gui.py`

## 这一页完成后，你应该能做到什么
- 完成 GUI 运行最小依赖安装

## 常见误区
- 只装 PyQt6，漏装串口或图像处理包

## 下一页
- [[06-软件环境搭建/06-安装PlatformIO]]
- [[12-GUI与上位机部分/04-如何启动GUI]]

## 导航
- 上一页：[[06-软件环境搭建/04-创建Python虚拟环境]]
- 下一页：[[06-软件环境搭建/06-安装PlatformIO]]
- 返回首页：[[00-首页/00-首页]]
