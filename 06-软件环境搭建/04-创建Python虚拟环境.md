# 创建Python虚拟环境

## 这一页是干什么的
让项目依赖隔离，避免系统环境被污染。

## 你会学到什么
- 虚拟环境是什么
- 如何创建和激活

## 先决条件
- [[06-软件环境搭建/03-Python安装]]

## 预计耗时
- 15 分钟

## 正文
在 `red-panda-afm/gui` 目录执行：
```bash
python -m venv .venv
source .venv/bin/activate
```
Windows PowerShell:
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

激活后会看到命令行前有 `(.venv)`。

## 用最简单的话再说一遍
虚拟环境就是给这个项目单独开一个“药箱”。

## 在 red-panda-afm 项目里它对应什么
- GUI 依赖安装都建议放在 `.venv`

## 这一页完成后，你应该能做到什么
- 创建并激活虚拟环境

## 常见误区
- 每次开终端忘记激活环境

## 下一页
- [[06-软件环境搭建/05-安装PyQt6等依赖]]

## 导航
- 上一页：[[06-软件环境搭建/03-Python安装]]
- 下一页：[[06-软件环境搭建/05-安装PyQt6等依赖]]
- 返回首页：[[00-首页/00-首页]]
