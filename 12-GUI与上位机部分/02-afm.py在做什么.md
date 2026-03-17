# afm.py在做什么

## 这一页是干什么的
详细解释 `afm.py` 的职责。它是 GUI 和固件之间真正的“通信与控制核心”。

## 你会学到什么
- `AFM` 类管理了哪些状态
- 串口收发是怎么实现的
- Focus/Approach/Scan 逻辑在这里怎么组织

## 先决条件
- [[12-GUI与上位机部分/01-gui项目总览]]
- [[02-零基础预备知识/05-串口通信是什么]]

## 预计耗时
- 40~60 分钟

## 正文

### 1. `AFM` 类是主入口
`afm.py` 定义了 `AFM` 类，主要负责：
- 串口端口发现、连接、关闭
- JSON 命令发送与响应等待
- 后台读取线程持续解析串口数据
- 当前状态管理（`IDLE/FOCUSING/APPROACHING/SCANNING`）

### 2. 串口读线程做了什么
在 `_serial_read_loop` 中，它会把每一行串口数据按类型分类：
- CSV 扫描数据：`x,y,adc_0,dac_z,is_trace`
- JSON 响应：放入 `response_queue`
- 其他文本：当作调试输出

这就是为什么你能在 GUI 里看到实时图像更新。

### 3. 关键高层方法
- `connect()` / `close()`：连接与关闭串口
- `send_and_receive()`：发送命令并等待返回
- `get_status()`：获取当前状态
- `focus()`：执行 focus 流程
- `approach()`：执行 approach 流程
- `start_scan()`：启动扫描流程
- `export_tiff()`：导出扫描结果

### 4. 数据组织（新手重点）
扫描数据被分别存到：
- `scan_data_trace`
- `scan_data_retrace`
- `scan_data`（合并视图）

这样 GUI 才能分别绘制 trace/retrace。

## 用最简单的话再说一遍
`afm.py` 就是“后台控制中枢”：负责连接设备、发命令、收数据、存结果。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm.py`

## 这一页完成后，你应该能做到什么
- 解释 `AFM` 类为什么是关键
- 能说清 CSV 与 JSON 两种串口数据用途

## 常见误区
- 把 `afm.py` 当成“只有工具函数”的小脚本
- 不理解读线程，导致误判实时显示问题

## 下一页
- [[12-GUI与上位机部分/03-afm_gui.py在做什么]]
- [[12-GUI与上位机部分/05-串口连接是怎么工作的]]

## 导航
- 上一页：[[12-GUI与上位机部分/01-gui项目总览]]
- 下一页：[[12-GUI与上位机部分/03-afm_gui.py在做什么]]
- 返回首页：[[00-首页/00-首页]]
