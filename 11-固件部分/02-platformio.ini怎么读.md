# platformio.ini怎么读

## 这一页是干什么的
手把手解释本项目 `platformio.ini` 的关键字段，让你知道“每一行在控制什么”。

## 你会学到什么
- `platform`、`board`、`framework` 含义
- 串口监视相关字段含义
- 依赖库字段怎么看

## 先决条件
- [[11-固件部分/01-firmware项目总览]]

## 预计耗时
- 25~35 分钟

## 正文
本项目关键配置（来自真实文件）：

```ini
[env:esp32doit-devkit-v1]
platform = espressif32
board = esp32doit-devkit-v1
framework = arduino
monitor_speed = 115200
monitor_echo = yes
monitor_filters = send_on_enter
lib_deps = 
	bblanchon/ArduinoJson@^7.3.1
```

### 逐行解释
- `[env:esp32doit-devkit-v1]`
  - 这是一个编译环境名字，你后续 Build/Upload 就对这个环境进行

- `platform = espressif32`
  - 使用 Espressif 的 ESP32 平台工具链

- `board = esp32doit-devkit-v1`
  - 编译参数按这个开发板定义来

- `framework = arduino`
  - 使用 Arduino 风格框架，不是 ESP-IDF 原生工程结构

- `monitor_speed = 115200`
  - 串口监视器默认波特率

- `lib_deps = bblanchon/ArduinoJson@^7.3.1`
  - 依赖 ArduinoJson 库（固件里处理 JSON 命令需要）

### 你现在该做的动作
- 打开这个文件，手动确认上述字段和你的环境一致
- 用自己的话写下：哪一行最容易配错，配错会怎样

## 用最简单的话再说一遍
`platformio.ini` 就是固件工程的“总开关设置表”。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/firmware/platformio.ini`

## 这一页完成后，你应该能做到什么
- 看懂本项目编译目标和串口配置
- 知道波特率不对会导致什么问题

## 常见误区
- 忽略 `board`，默认任何 ESP32 都一样
- 串口监视器波特率和固件配置不一致

## 下一页
- [[11-固件部分/03-ESP32在这个项目里负责什么]]
- [[11-固件部分/04-如何编译固件]]

## 导航
- 上一页：[[11-固件部分/01-firmware项目总览]]
- 下一页：[[11-固件部分/03-ESP32在这个项目里负责什么]]
- 返回首页：[[00-首页/00-首页]]
