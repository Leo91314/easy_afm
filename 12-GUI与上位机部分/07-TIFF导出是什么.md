# TIFF导出是什么

## 这一页是干什么的
解释为什么 GUI 里要导出 TIFF，以及导出文件里包含什么。

## 你会学到什么
- TIFF 在本项目里的用途
- 导出时会生成哪些文件
- 元数据（metadata）有什么价值

## 先决条件
- [[12-GUI与上位机部分/06-扫描数据大概长什么样]]

## 预计耗时
- 25~35 分钟

## 正文
在 `afm.py` 的 `export_tiff()` 里，导出逻辑大致是：
- 为 trace/retrace 两种扫描分别导出
- 为 ADC0 与 DACZ 两个通道分别导出
- 同时写一个 `scan_metadata.json`

常见输出文件（按代码命名规则）：
- `trace_ADC0.tiff`
- `trace_DACZ.tiff`
- `retrace_ADC0.tiff`
- `retrace_DACZ.tiff`
- `scan_metadata.json`

元数据里会写：
- 扫描参数（x/y范围、分辨率）
- 每个图像的 NaN 比例、最小值、最大值

这让你后续可以回看“这张图当时怎么来的”。

## 用最简单的话再说一遍
TIFF 是“结果图”，metadata 是“实验说明书”，两者缺一不可。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/afm.py` 的 `export_tiff()`
- `red-panda-afm/gui/afm_gui.py` 的 `save_scan_data()`

## 这一页完成后，你应该能做到什么
- 知道导出文件通常有哪些
- 理解为什么要保留 metadata

## 常见误区
- 只保存图像，不保存参数信息
- 导出后不检查文件是否完整

## 下一页
- [[12-GUI与上位机部分/08-第一次打开GUI要检查什么]]
- [[18-模板与记录/04-实验记录模板]]

## 导航
- 上一页：[[12-GUI与上位机部分/06-扫描数据大概长什么样]]
- 下一页：[[12-GUI与上位机部分/08-第一次打开GUI要检查什么]]
- 返回首页：[[00-首页/00-首页]]
