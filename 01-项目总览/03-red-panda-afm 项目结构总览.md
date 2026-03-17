# red-panda-afm 项目结构总览

## 这一页是干什么的
把仓库目录翻译成“人话”，让你知道每个目录要在复现中做什么。

## 你会学到什么
- `cad / firmware / gui / pcb` 各是什么
- 先读哪块、后做哪块
- 当前仓库资料的完整度现状

## 先决条件
- [[01-项目总览/01-这个项目到底是什么]]

## 预计耗时
- 20~30 分钟

## 正文
根据当前仓库扫描，核心结构如下：

| 目录 | 作用 | 当前看到的内容 | 你现在该做什么 |
|---|---|---|---|
| `cad/` | 机械设计 | `afm/` 下有 `.step`、`.3mf`、`AFM v1.f3z`、截图 PNG | 先学会读文件类型，不急着全量打印 |
| `firmware/` | 下位机固件 | `platformio.ini`、`src/main.cpp`、自定义 ADC/DAC 库 | 先能编译，理解命令和状态机 |
| `gui/` | 上位机界面 | `afm.py`、`afm_gui.py`、PyQt UI 文件 | 先搭 Python 环境并启动 GUI |
| `pcb/` | 电路工程 | 一个 EasyEDA Pro 工程包 `.epro` | 先确认能否导出 BOM/Gerber/PnP |

从 `firmware/platformio.ini` 可确认：
- 使用 PlatformIO
- 目标板为 `esp32doit-devkit-v1`
- 波特率 `115200`

从 `gui` 源码可确认：
- 依赖 `PyQt6`、`pyqtgraph`、`pyserial`、`numpy`、`tifffile`
- 包含 Focus / Approach / Scan 相关界面流程

## 用最简单的话再说一遍
这个仓库像一台机器被拆成四个抽屉：机械、固件、GUI、电路。你要按顺序逐个搞定，不要四个一起上。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/cad/`
- `red-panda-afm/firmware/`
- `red-panda-afm/gui/`
- `red-panda-afm/pcb/`

## 这一页完成后，你应该能做到什么
- 看见目录不会慌
- 知道“先软件后硬件”的合理顺序
- 能指出项目资料当前并不完整

## 常见误区
- 一上来打开 `pcb` 就开始下单制板
- 没看 `platformio.ini` 就默认 MCU 是 Arduino UNO
- 以为 `BUILD_GUIDE` 已经覆盖全部细节

## 下一页
- [[01-项目总览/04-这个项目复现难在哪里]]
- [[03-仓库阅读与信息提取/02-仓库目录逐个解释]]
- [[04-复现总计划/01-总阶段划分]]

## 导航
- 上一页：[[01-项目总览/02-AFM 是什么]]
- 下一页：[[01-项目总览/04-这个项目复现难在哪里]]
- 返回首页：[[00-首页/00-首页]]
