# firmware项目总览

## 这一页是干什么的
带你从零理解 `red-panda-afm` 的固件（firmware）到底负责什么、怎么和 GUI 配合、为什么它是硬件复现的核心。

## 你会学到什么
- 固件在整套系统中的角色
- 本项目固件目录结构
- 固件处理命令的大致范围
- 新手应该先掌握哪几件事

## 先决条件
- [[01-项目总览/03-red-panda-afm 项目结构总览]]
- [[02-零基础预备知识/04-单片机与ESP32入门]]

## 预计耗时
- 30~45 分钟

## 正文

你可以把固件理解成“控制板的大脑程序”。

在本项目里，固件主要做这些事：
1. 接收上位机（GUI）发来的 JSON 命令
2. 控制硬件（DAC、ADC、步进电机）
3. 管理状态机（`IDLE / FOCUSING / APPROACHING / SCANNING`）
4. 通过串口返回状态、数据、错误信息

### 固件目录怎么读
- `red-panda-afm/firmware/platformio.ini`
  - 编译目标、平台、串口监视配置
- `red-panda-afm/firmware/src/main.cpp`
  - 主逻辑、命令处理、状态机、控制流程
- `red-panda-afm/firmware/lib/AD5761`、`lib/ADS8681`、`lib/ads868x`
  - 与 DAC/ADC 相关的驱动封装

### 你能确认的事实（不是猜测）
- 固件使用 PlatformIO
- 目标板环境是 `esp32doit-devkit-v1`
- 串口监视常用速率是 `115200`
- 代码里确实有 `scan/approach/pid_control/set_dac/get_status` 等命令分支

### 对新手最重要的顺序
1. 先能编译（不急烧录）
2. 再能烧录
3. 再能看串口状态
4. 最后再去做复杂流程（scan/approach）

## 用最简单的话再说一遍
固件就是“控制板会不会按指令工作”的关键。先让它稳定，再做扫描。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/firmware/platformio.ini`
- `red-panda-afm/firmware/src/main.cpp`
- `red-panda-afm/firmware/lib/*`

## 这一页完成后，你应该能做到什么
- 能解释固件在系统里的作用
- 知道固件目录先看哪几个文件
- 知道下一步先去看 `platformio.ini`

## 常见误区
- 只会点“Upload”，不知道固件在做什么
- 硬件问题和固件问题不区分

## 下一页
- [[11-固件部分/02-platformio.ini怎么读]]
- [[11-固件部分/03-ESP32在这个项目里负责什么]]

## 导航
- 上一页：[[10-执行器与运动控制/05-为什么不能一上来就直接扫描]]
- 下一页：[[11-固件部分/02-platformio.ini怎么读]]
- 返回首页：[[00-首页/00-首页]]
