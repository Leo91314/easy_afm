# firmware目录怎么读

## 这一页是干什么的
告诉你如何从固件目录中提取“控制架构”和“调试入口”。

## 你会学到什么
- PlatformIO 和 ESP32 的对应关系
- `main.cpp` 的核心功能块
- 命令通信大致结构

## 先决条件
- [[03-仓库阅读与信息提取/02-仓库目录逐个解释]]
- [[06-软件环境搭建/06-安装PlatformIO]]

## 预计耗时
- 30~45 分钟

## 正文
已确认：
- `platformio.ini` 指向 `esp32doit-devkit-v1`
- 串口监视波特率为 `115200`
- `src/main.cpp` 中有状态机：`IDLE / FOCUSING / APPROACHING / SCANNING`
- 固件处理 JSON 命令（如 `reset`、`get_status`、`scan`、`approach`、`pid_control`）
- 使用自定义 DAC/ADC 库（`AD5761`、`ADS8681`）

这意味着：
- GUI 与固件是通过串口协议协同
- 你要重点理解状态、命令、返回值，而不仅是编译通过

## 用最简单的话再说一遍
固件就是“机器大脑”。先学会跟它“说话”（串口命令），再学怎么调它。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/firmware/platformio.ini`
- `red-panda-afm/firmware/src/main.cpp`
- `red-panda-afm/firmware/lib/*`

## 这一页完成后，你应该能做到什么
- 说出固件目标板和串口速率
- 识别主要状态和命令

## 常见误区
- 只会烧录，不会读串口日志
- 不知道当前系统处于哪个状态就乱发命令

## 下一页
- [[11-固件部分/01-firmware项目总览]]
- [[11-固件部分/02-platformio.ini怎么读]]
- [[03-仓库阅读与信息提取/05-gui目录怎么读]]

## 导航
- 上一页：[[03-仓库阅读与信息提取/03-cad目录怎么读]]
- 下一页：[[03-仓库阅读与信息提取/05-gui目录怎么读]]
- 返回首页：[[00-首页/00-首页]]
