# Cloud and Big Data Labs

云计算与大数据处理实验代码，供个人课程学习与复现使用。仓库只保存代码、依赖和必要配置，不保存实验报告、运行截图、身份记录、原始运行数据或虚拟环境。

## 目录

- `coursekit/`：课程实验01—08的公共运行框架。
- `labs/lab01/`：实验一原始基线、修改对象键、修改payload的三个阶段副本。
- 各实验目录中的 `附件/`：课程练习脚手架和配置。
- `tests/`：课程提供的测试。
- `requirements.lock.txt`：Windows / Python 3.12锁定依赖。

目前本仓库提供实验一的个人变式，其他实验框架和附件不代表个人已完成相应实验。

## 实验一复现

在仓库根目录使用PowerShell：

```powershell
$env:PYTHONUTF8 = '1'
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.lock.txt
.\.venv\Scripts\python.exe -m pip check
$studentId = Read-Host '请输入本人学号'
.\.venv\Scripts\python.exe -m coursekit identity --student-id $studentId --lab 01 --stage start
.\.venv\Scripts\python.exe -m coursekit seed --rows 20000
.\.venv\Scripts\python.exe -m coursekit lab01
.\.venv\Scripts\python.exe .\labs\lab01\manual_baseline.py
.\.venv\Scripts\python.exe .\labs\lab01\manual_key.py
.\.venv\Scripts\python.exe .\labs\lab01\manual_payload.py
```

本实验使用本机Moto模拟S3 HTTP服务，测试凭据不具备真实云权限。执行结果在本地产生，未上传到此仓库。

## 代码来源

公共框架、测试及原始练习附件来自课程仓库：
https://gitee.com/ryukinkou/BDP/

本地课程基准版本：`32e5cd61f58c9bd4c41b87fb9c2940912fc693b8`。
保留原作者归属；个人阶段副本以课程附件为基础。仓库不将课程框架声明为本人独立编写。
