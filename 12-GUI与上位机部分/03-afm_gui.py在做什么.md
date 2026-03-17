# afm_gui.py在做什么

## 这一页是干什么的
解释 `afm_gui.py` 如何把 `afm.py` 的能力变成你可操作的窗口和按钮。

## 你会学到什么
- 主窗口和子窗口结构
- Focus/Approach/Scan 页面分别做什么
- GUI 定时刷新机制

## 先决条件
- [[12-GUI与上位机部分/02-afm.py在做什么]]

## 预计耗时
- 40~60 分钟

## 正文
`afm_gui.py` 里主要有这些类：

- `MainWindow`
  - 串口连接
  - DAC 控制
  - PID 参数设置
  - 打开子窗口（Focus/Approach/Scan）

- `FocusWidget`
  - 启动 focus 扫描
  - 绘制 `ADC vs DAC_F`
  - 显示 optimal focus

- `ApproachWidget`
  - 设置 motor/step/threshold/speed
  - 实时画接近过程数据

- `ScanWidget`
  - 设置扫描范围和分辨率
  - 显示二维图像
  - 保存数据（调用 `export_tiff`）

### 为什么 GUI 会“实时更新”
多个窗口都用了 `QTimer` 定时调用更新函数（例如每 100ms），
从 `afm.py` 读取最新状态/数据后刷新图和控件。

## 用最简单的话再说一遍
`afm_gui.py` 是“操作面板”，把后台逻辑变成按钮、曲线和图像。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm_gui.py`
- `red-panda-afm/gui/ui/*.ui`

## 这一页完成后，你应该能做到什么
- 说出主窗口和三个子窗口的职责
- 理解为什么 GUI 需要定时刷新

## 常见误区
- 只看界面事件，不看背后调用 `afm.py`
- 窗口卡顿就直接怀疑固件

## 下一页
- [[12-GUI与上位机部分/04-如何启动GUI]]
- [[12-GUI与上位机部分/08-第一次打开GUI要检查什么]]

## 导航
- 上一页：[[12-GUI与上位机部分/02-afm.py在做什么]]
- 下一页：[[12-GUI与上位机部分/04-如何启动GUI]]
- 返回首页：[[00-首页/00-首页]]
