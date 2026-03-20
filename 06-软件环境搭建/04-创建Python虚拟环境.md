# 创建Python虚拟环境

## 这一页是干什么的
把 GUI 依赖隔离到项目内，保证复现结果可复制、可迁移、可回滚。

## 你会学到什么
- 为什么必须在 `red-panda-afm/gui` 单独建 venv
- 跨平台激活命令和包安装方式
- 如何固化环境快照

## 先决条件
- [[06-软件环境搭建/03-Python安装]]

## 预计耗时
- 20~35 分钟

## 正文
### 原理先讲清
同一台电脑上常有多个 Python 项目。虚拟环境把依赖锁在当前项目，避免“昨天能跑今天不能跑”。

### 一步一步怎么做
1. 进入 GUI 目录：
   ```bash
   cd red-panda-afm/gui
   ```
2. 创建虚拟环境：
   ```bash
   python -m venv .venv
   ```
3. 激活虚拟环境：
   - macOS/Linux:
     ```bash
     source .venv/bin/activate
     ```
   - Windows PowerShell:
     ```powershell
     .\.venv\Scripts\Activate.ps1
     ```
4. 升级 pip：
   ```bash
   python -m pip install --upgrade pip
   ```
5. 记录当前环境快照：
   ```bash
   python -m pip freeze > requirements-local.txt
   ```

### 每一步完成后怎么检查
- 终端提示符出现 `(.venv)`。
- `python -c "import sys; print(sys.prefix)"` 指向 `.venv`。
- `requirements-local.txt` 能生成。

### 出错时先看哪里
- 激活脚本执行被拦截：Windows 需调整执行策略。
- 激活后仍是全局 Python：检查终端是否重新打开、路径是否正确。

### 暂时做不到也没关系的部分
- `requirements-local.txt` 先空也没关系，下一页安装依赖后再刷新。

## 用最简单的话再说一遍
虚拟环境就是你的“项目隔离舱”，不进舱就别装依赖。

## 在 red-panda-afm 项目里它对应什么
- `red-panda-afm/gui/`

## 这一页完成后，你应该能做到什么
- 独立创建并激活项目专属 Python 环境
- 避免全局包污染导致的隐蔽故障

## 常见误区
- 在仓库根目录建一个 venv 给所有子项目混用
- 忘记激活 venv 就直接 `pip install`

## 下一页
- [[06-软件环境搭建/05-安装PyQt6等依赖]]
- [[06-软件环境搭建/09-如何打开gui项目]]

## 导航
- 上一页：[[06-软件环境搭建/03-Python安装]]
- 下一页：[[06-软件环境搭建/05-安装PyQt6等依赖]]
- 返回首页：[[00-首页/00-首页]]
