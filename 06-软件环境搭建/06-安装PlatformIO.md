# 安装PlatformIO

## 这一页是干什么的
完成 ESP32 固件构建链路安装，让你能在本机编译 `firmware`。

## 你会学到什么
- PlatformIO 在本项目里的作用
- VSCode 插件方式与命令行方式安装
- 编译成功的最低验收标准

## 先决条件
- [[06-软件环境搭建/05-安装PyQt6等依赖]]
- [[06-软件环境搭建/07-安装VSCode与必要插件]]

## 预计耗时
- 30~60 分钟（首次会下载工具链）

## 正文
### 原理先讲清
固件工程不是 Arduino IDE 单文件模型，而是 PlatformIO 项目，核心配置在：
`red-panda-afm/firmware/platformio.ini`

关键环境：
- 平台：`espressif32`
- 板卡：`esp32doit-devkit-v1`
- 串口监视器：`115200`

### 安装路径
1. VSCode 插件安装 PlatformIO（推荐新手）。
2. 如需命令行：
   ```bash
   python -m pip install -U platformio
   ```

### 一步一步怎么做
1. 打开 `red-panda-afm/firmware`。
2. 等 PlatformIO 自动解析 `platformio.ini`。
3. 执行首次编译（会下载大量工具链）：
   ```bash
   cd red-panda-afm/firmware
   pio run
   ```
4. 保存编译日志到 `logs/firmware-build/`。

### 每一步完成后怎么检查
- `pio run` 结束为 `SUCCESS`。
- 没有“找不到 board/platform”类错误。
- 可以看到依赖库如 `ArduinoJson` 被正确解析。

### 出错时先看哪里
- `pio: command not found`：命令行未安装或 PATH 未生效。
- 下载失败：网络问题，重试并保持稳定连接。
- 板卡不匹配：确认 `platformio.ini` 是否被误改。

### 暂时做不到也没关系的部分
- 没有实体板时可先不烧录，只做编译链路通过。

## 用最简单的话再说一遍
PlatformIO 是固件入口，先让它编译通过，再谈烧录和串口联调。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/firmware/platformio.ini`
- `red-panda-afm/firmware/src/main.cpp`

## 这一页完成后，你应该能做到什么
- 在本机独立完成固件编译
- 识别平台配置错误与网络下载错误

## 常见误区
- 在仓库根目录直接跑 `pio run`
- 修改配置后不记录，后续无法回滚

## 下一页
- [[06-软件环境搭建/08-如何打开firmware项目]]
- [[11-固件部分/04-如何编译固件]]

## 导航
- 上一页：[[06-软件环境搭建/05-安装PyQt6等依赖]]
- 下一页：[[06-软件环境搭建/07-安装VSCode与必要插件]]
- 返回首页：[[00-首页/00-首页]]
