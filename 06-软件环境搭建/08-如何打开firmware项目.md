# 如何打开firmware项目

## 这一页是干什么的
把 `firmware` 工程从“能看到源码”推进到“能编译、能监视串口、能发命令”。

## 你会学到什么
- `platformio.ini` 的关键配置怎么读
- 固件编译与串口监视的标准操作
- 与 GUI 协同联调时的注意点

## 先决条件
- [[06-软件环境搭建/06-安装PlatformIO]]
- [[11-固件部分/02-platformio.ini怎么读]]

## 预计耗时
- 35~60 分钟

## 正文
### 原理先讲清
`firmware` 是独立 PlatformIO 项目，入口在 `src/main.cpp`。所有控制命令都经 `processCommand()` 接收 JSON，再驱动 DAC/ADC/步进状态机。

### 一步一步怎么做
1. 在 VSCode 打开 `red-panda-afm/firmware`。
2. 检查 `platformio.ini`：
   - `board = esp32doit-devkit-v1`
   - `monitor_speed = 115200`
3. 编译：
   ```bash
   cd red-panda-afm/firmware
   pio run
   ```
4. 若有硬件，连接后监视串口：
   ```bash
   pio device monitor -b 115200
   ```
5. 用串口发送一条命令（以换行结尾）：
   ```json
   {"command":"get_status"}
   ```

### 每一步完成后怎么检查
- 编译产物生成，显示 `SUCCESS`。
- 串口监视器看到初始化输出（如 serial initialized）。
- `get_status` 返回包含 `adc_0`、`dac_x`、`state` 等字段。

### 出错时先看哪里
- 串口打开失败：端口占用、线缆仅充电不传输。
- 没有 JSON 回复：命令缺少换行或 JSON 语法错误。
- 频繁重启：优先排查供电和地线。

### 暂时做不到也没关系的部分
- 无硬件可先完成“编译 + 代码阅读 + 命令协议理解”。

## 用最简单的话再说一遍
能编译只是第一步；能发命令并收状态，才算打开了固件工程。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/firmware/platformio.ini`
- `red-panda-afm/firmware/src/main.cpp`

## 这一页完成后，你应该能做到什么
- 独立构建固件并验证命令接口
- 为 GUI 联调提供可用固件基线

## 常见误区
- 把 `read_adc` 当作唯一状态接口（应优先看 `get_status`）
- 忘记 JSON 换行导致固件一直不解析命令

## 下一页
- [[06-软件环境搭建/09-如何打开gui项目]]
- [[11-固件部分/06-串口监视器怎么用]]

## 导航
- 上一页：[[06-软件环境搭建/07-安装VSCode与必要插件]]
- 下一页：[[06-软件环境搭建/09-如何打开gui项目]]
- 返回首页：[[00-首页/00-首页]]
